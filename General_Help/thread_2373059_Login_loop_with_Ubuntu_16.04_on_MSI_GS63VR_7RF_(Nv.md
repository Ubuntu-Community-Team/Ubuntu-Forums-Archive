---
title: "Login loop with Ubuntu 16.04 on MSI GS63VR 7RF (Nvidia GTX 1060)"
date: 2017-10-02
forum: General Help
---

### Post by circuitbreaker2 on 2017-10-02
Good afternoon everybody,

I am the owner of a notebook made by MSI (model GS63VR 7RF) with a dual boot setup with Windows 10 and Ubuntu 16.04 LTS. Secure boot and fast boot are disabled. Until yesterday, both OS were working fine.

Now when I try to boot on Ubuntu, the login screen loops every time I am asked for my password and do "enter".
After looking online, it seems that this problem is linked to the GPU, and that it happened after an automatic update from version 375 of the Nvidia driver to the version 384. 

I can boot in graphics safe mode and open a terminal. I have tried to purge the drivers and switch back to version 375 (following [this forum link]("https://askubuntu.com/questions/862943/login-infinite-loop-after-installing-an-nvidia-driver")) but it did not change anything. I also tried to switch to the Intel-integrated GPU with "sudo prime-select intel" but this makes the problem even worse as I cannot even see a login screen. 


[LIST]
[*]Could my problem be due to the fact that I am using the 16.04 LTS version of Ubuntu and not the 17.04?
[/LIST]

[LIST]
[*]Is a sudo apt-get purge nvidia*, autoclean, autoremove nvidia*, add-apt-repository ppa:graphics-drivers/ppa, update, autoinstall, reboot the best way to install the driver for Nvidia? Is the latest one really recommended like it is written?
[/LIST]

[LIST]
[*]Should I use the "official" Intel graphics from linux website [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads) to install the drivers and firmware for my machine?
[/LIST]

Many thanks in advance for any help and I would be happy to provide further tests/benchmark.

---

### Post by liorhakim on 2017-10-08
the following worked for me:

        sudo apt-get install --reinstall ca-certificates
	sudo apt-get update
	sudo apt purge 'nvidia.*'
	sudo add-apt-repository ppa:graphics-drivers/ppa
	sudo apt update
	sudo apt-get install nvidia-375
	reboot

that work when i first installed

after that i updated to version 384.90 with no apperant problems

also can check my detailed install here [https://github.com/0i0/MSI-GS63VR_Ubuntu]("https://github.com/0i0/MSI-GS63VR_Ubuntu")

---

### Post by nemorigolo on 2018-01-16
Hi,

I have the same PC and the install was not easy. Many problems but I have a good install now.
I give you all commands for a complete install. Note that it's not working with Ubuntu 17.10 because of Wayland (NVidia drivers are not compatible yet). But it works with xUbuntu 17.10 (xOrg server).

So :
Install Ubuntu 16.04 or xUbuntu 17.10
After reboot (with ethernet cable inserted), don't login and tap Ctrl+Alt+F4
Log with your user

Install NVidia drivers :
sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt install nvidia-387

use prime for select card at login (sudo prime-select intel or sudo prime-select nvidia)

Fix Killer 1535 Wifi card :
wget [http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.170_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.170_all.deb)
sudo dpkg -i linux-firmware*.deb
sudo modprobe -r ath10k_pci && sudo modprobe ath10k_pci

Add in grub (sudo nano /etc/default/grub) :
GRUB_CMDLINE_LINUX_DEFAULT : acpi_osi=! acpi_osi=&#8216;Windows 2009&#8217;
GRUB_GFXMODE=1920x1080x32
GRUB_GFXPAYLOAD_LINUX=keep

sudo update-grub

Reboot. And you could use your PC with Ubuntu.
Add Intel microcode in Proprietary Driver Panel

For msi keayboard color, install msi-keyboard
Create a script like :
#!/bin/bash
msi-keyboard -m normal -c left,red,high
msi-keyboard -m normal -c middle,yellow,high
msi-keyboard -m normal -c right,blue,high

And launch at session startup

That's all

---

