---
title: "xterm error when installing Multisystem for multiboot flash drive"
date: 2021-03-04
forum: General Help
---

### Post by webmanoffesto on 2021-03-04
I want to install Multisystem so I can create a multiboot flash drive. But I'm getting an exterm error. I tried using XFCE Terminal and I still get the same error.

$ sudo ./install-depot-multisystem.sh
[sudo] password for tom: 


 Error: xterm 

I'm on Ubuntu 20.04.2
64 Bit

I'm able to plug my flash drive into the USB port.
I'm able to navigate to /media/tom/Ubuntu20.
But none of the software like Brassero is able to write to it.

Even right clicking on HBCD_PE_x64.iso and selecting write to disk doesn't work. It won't write to the flash drive. It says no disk available.

---

### Post by Holger_Gehrke on 2021-03-04
Is [this]("https://gist.github.com/gene1wood/3cd74ba84a02886641db") the script you're trying to use ? It calls 'xterm' directly instead of going through the symbolic link 'x-terminal-emulator' (which is available on all Debian based distributions since it's part of the debian-alternatives system). So if you don't have xterm installed on your system it fails.

All the script does is add 'deb [http://liveusb.info/multisystem/depot](http://liveusb.info/multisystem/depot) all main' to your /etc/apt/sources.list, add 'http://liveusb.info/multisystem/depot/multisystem.asc' to the keys known to apt, update the list of available package (apt-get update) and then install a package named 'MultiSystem'.

Brassero and whatever program gets called when you select 'Write to Disk' both try to write the image to CD or DVD because that's what ISO-images where originally for. To write such an image to a flash drive you need a different program - the Startup Disk Creator or unetbootin or Balena Etcher or if you're feeling adventurous - or have lots and lots of experience and nothing to lose ... - dd (aka Data Dump aka Disk Destroyer ... ). None of these on their own can do what Multiboot is supposed to do - take multiple OS-Images, put them all on one USB drive and allow you to select during booting which OS to boot from the stick.

Holger

---

