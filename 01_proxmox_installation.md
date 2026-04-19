# 1 Proxmox (9.1.7) by the time of the creation of this file, installation of Windows Server 2025 Standard (with GUI)

## Description of VM paramaters

- General
  - Name: something descriptive "DC01"
  - Resource Pool: not used
- OS
  - ISO image: see where is installation media (ISO file)
  - Type: for compatability choose what OS family (Microsoft Windows)
  - Version: 11/2022/2025
  - IMPORTANT NOTE: select "Add additional drive for VirIO drivers", you will need these drivers for your installation
  - after selection you will choose which storage and what image you will mount
  - if you don't have such image look Google for `virtio-win.iso`
- System
  - leave q35 for Machine
  - choose your target disk where the VM disk will be stored for EFI Storage
  - SCSI Controller - VirtIO SCSI single (SCSI has better performance)
  - Qemu Agent - you need that so check the box
  - Add TPM - another check here
  - TPM storage again your target disk is the same place where the VM disk resides
- Disks
  - Bus/Device - be sure SCSI is selected (leave device as 0)
  - Storage: your target disk, be sure to choose LVM-Thin as it has better performance than LVM for VM disks
  - Disk size: it depends on your hardware of course but my recommendation is for anything greater than 80 gigs
  - if you have SSD you can also check Discard option
- CPU
  - Sockets: generally 1 is enough
  - Cores: nothing less than 2
  - Type: will vary depending on the hardware so nothing hard set here
- Memory
  - if standard edition with GUI good idea is 8 gigs+
  - if standard edition without GUI (core edition) maybe you can succeed with just 4 gigs
- Network
  - you pick your configuration here, if nothing fancy in mind you can go with the defaults
- Confirm tab
  - Check again your config before installation and check the box for `Start after created`
- When the VM is created, given that you are in the console mode for your VM, the installation will wait for you to boot from media and afterwards to press any key to start installation process