#
# This Vagrant file is to set the Puppet master to
# install an agent with all minimun requirements we
# need. 
#
# config.vm = modify the configuration of the machine that Vagrant manages.
# config.ssh = relate to configuring how Vagrant will access your machine over SSH
# config.vagrant = modify the behavior of Vagrant itself.
#
# Ref.:
# https://www.vagrantup.com/docs/vagrantfile/version.html
#

Vagrant.configure("2") do |config|

  config.vm.box =  "debian/stretch64"

  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
  end

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end

  config.vm.synced_folder ".", "/vagrant"

  config.vm.provision "shell", :path => "install_Common.sh", :name => "Installing common tools to all VMs"

  # First master puppet: Jilata
  config.vm.define :master do |master|
    master.vm.network "private_network", ip: "192.168.10.10"
	master.vm.hostname = "jilata"
  end

  # An agent for testing
  config.vm.define :agent do |agent|
    agent.vm.network "private_network", ip: "192.168.10.12"
	agent.vm.hostname = "agent"
  end

end



