Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
  end


  config.vm.network :private_network, ip: "192.168.111.3"
  # Install latest Docker version
  config.vm.provision "docker"
  # Install django and docker-compose
  config.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/vagrant.yml"
      ansible.inventory_path = "ansible/inventories/production"
      ansible.limit = 'all'
      ansible.extra_vars = {
        ansible_ssh_user: 'vagrant'
      }
  end

end