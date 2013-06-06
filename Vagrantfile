# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define :mq1 do |mq1|

    mq1.vm.hostname = "rabbitmq-berkshelf-1"

    # Every Vagrant virtual environment requires a box to build off of.
    mq1.vm.box = "precise64_squishy_2013-02-09"

    # The url from where the 'config.vm.box' box will be fetched if it
    # doesn't already exist on the user's system.
    mq1.vm.box_url = "https://s3-us-west-2.amazonaws.com/squishy.vagrant-boxes/precise64_squishy_2013-02-09.box"

    # Assign this VM to a host-only network IP, allowing you to access it
    # via the IP. Host-only networks can talk to the host machine as well as
    # any other machines on the same network, but cannot be accessed (through this
    # network interface) by any external networks.
    mq1.vm.network :private_network, ip: "33.33.33.11"

    # Create a public network, which generally matched to bridged network.
    # Bridged networks make the machine appear as another physical device on
    # your network.

    # config.vm.network :public_network

    # Create a forwarded port mapping which allows access to a specific port
    # within the machine from a port on the host machine. In the example below,
    # accessing "localhost:8080" will access port 80 on the guest machine.

    # Share an additional folder to the guest VM. The first argument is
    # the path on the host to the actual folder. The second argument is
    # the path on the guest to mount the folder. And the optional third
    # argument is a set of non-required options.
    # config.vm.synced_folder "../data", "/vagrant_data"

    # Provider-specific configuration so you can fine-tune various
    # backing providers for Vagrant. These expose provider-specific options.
    # Example for VirtualBox:
    #
    # config.vm.provider :virtualbox do |vb|
    #   # Don't boot with headless mode
    #   vb.gui = true
    #
    #   # Use VBoxManage to customize the VM. For example to change memory:
    #   vb.customize ["modifyvm", :id, "--memory", "1024"]
    # end
    #
    # View the documentation for the provider you're using for more
    # information on available options.

    config.ssh.max_tries = 40
    config.ssh.timeout   = 120

    # The path to the Berksfile to use with Vagrant Berkshelf
    # config.berkshelf.berksfile_path = "./Berksfile"

    # Enabling the Berkshelf plugin. To enable this globally, add this configuration
    # option to your ~/.vagrant.d/Vagrantfile file
    config.berkshelf.enabled = true

    # An array of symbols representing groups of cookbook described in the Vagrantfile
    # to exclusively install and copy to Vagrant's shelf.
    # config.berkshelf.only = []

    # An array of symbols representing groups of cookbook described in the Vagrantfile
    # to skip installing and copying to Vagrant's shelf.
    # config.berkshelf.except = []

    mq1.vm.provision :chef_client do |chef|
      chef.chef_server_url        = "https://chef.audax.in"
      chef.validation_client_name = "chef-validator"
      chef.validation_key_path    = "/Users/scalp/audax/chef/.chef/chef-validator.pem"

      chef.environment = "debug"

      chef.run_list = [
          "role[rabbitmq_cluster]"
        ]
      end
    end

    config.vm.define :mq2 do |mq2|

      mq2.vm.hostname = "rabbitmq-berkshelf-2"

      # Every Vagrant virtual environment requires a box to build off of.
      mq2.vm.box = "precise64_squishy_2013-02-09"

      # The url from where the 'config.vm.box' box will be fetched if it
      # doesn't already exist on the user's system.
      mq2.vm.box_url = "https://s3-us-west-2.amazonaws.com/squishy.vagrant-boxes/precise64_squishy_2013-02-09.box"

      # Assign this VM to a host-only network IP, allowing you to access it
      # via the IP. Host-only networks can talk to the host machine as well as
      # any other machines on the same network, but cannot be accessed (through this
      # network interface) by any external networks.
      mq2.vm.network :private_network, ip: "33.33.33.12"

      # Create a public network, which generally matched to bridged network.
      # Bridged networks make the machine appear as another physical device on
      # your network.

      # config.vm.network :public_network

      # Create a forwarded port mapping which allows access to a specific port
      # within the machine from a port on the host machine. In the example below,
      # accessing "localhost:8080" will access port 80 on the guest machine.

      # Share an additional folder to the guest VM. The first argument is
      # the path on the host to the actual folder. The second argument is
      # the path on the guest to mount the folder. And the optional third
      # argument is a set of non-required options.
      # config.vm.synced_folder "../data", "/vagrant_data"

      # Provider-specific configuration so you can fine-tune various
      # backing providers for Vagrant. These expose provider-specific options.
      # Example for VirtualBox:
      #
      # config.vm.provider :virtualbox do |vb|
      #   # Don't boot with headless mode
      #   vb.gui = true
      #
      #   # Use VBoxManage to customize the VM. For example to change memory:
      #   vb.customize ["modifyvm", :id, "--memory", "1024"]
      # end
      #
      # View the documentation for the provider you're using for more
      # information on available options.

      config.ssh.max_tries = 40
      config.ssh.timeout   = 120

      # The path to the Berksfile to use with Vagrant Berkshelf
      # config.berkshelf.berksfile_path = "./Berksfile"

      # Enabling the Berkshelf plugin. To enable this globally, add this configuration
      # option to your ~/.vagrant.d/Vagrantfile file
      config.berkshelf.enabled = true

      # An array of symbols representing groups of cookbook described in the Vagrantfile
      # to exclusively install and copy to Vagrant's shelf.
      # config.berkshelf.only = []

      # An array of symbols representing groups of cookbook described in the Vagrantfile
      # to skip installing and copying to Vagrant's shelf.
      # config.berkshelf.except = []

      mq2.vm.provision :chef_client do |chef|
        chef.chef_server_url        = "https://chef.audax.in"
        chef.validation_client_name = "chef-validator"
        chef.validation_key_path    = "/Users/scalp/audax/chef/.chef/chef-validator.pem"

        chef.environment = "debug"

        chef.run_list = [
            "role[rabbitmq_cluster]"
          ]
        end
      end
end
