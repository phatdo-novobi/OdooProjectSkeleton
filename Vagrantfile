# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "novobi/odoo-box"
  config.vm.hostname = "odoo-vagrant"
  config.vm.network "private_network", type: "dhcp"
  config.vm.synced_folder ".", "/opt/odoo", owner: "odoo", group: "odoo", :mount_options => ["dmode=777", "fmode=777"]
  config.vm.provision "shell", inline: "hostname -I | cut -d' ' -f2", run: "always"
  #workaround for issue with xenial base box
  config.vm.provider "virtualbox" do |vb|
    vb.customize [ "modifyvm", :id, "--uartmode1", "disconnected" ]
  end
end
