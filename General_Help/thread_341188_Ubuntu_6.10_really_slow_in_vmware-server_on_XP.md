---
title: "Ubuntu 6.10 really slow in vmware-server on XP"
date: 2007-01-18
forum: General Help
---

### Post by freddo on 2007-01-18
Hi, new and fresh XP on fast laptop with vmware-server and a new install of Ubuntu 6.10, vmware-tools also installed and running.

But,, the ubuntu machine is really slow and require a lot of cpu from XP, especially when just moving items on the Ubuntu desktop, like a terminal. 

Does anyone have any ideas?

/Freddo

---

### Post by ser1alsn1per on 2007-01-18
when u go into the settings for vmware server give more ram to ubuntu also if you have dual core u can give it 2 processors                              why dont u run them the other way arround or dual boot?

---

### Post by Hanzerik on 2007-01-19
Try using just VMWare Player to install Ubuntu

Make a folder on your desktop called UbuntuVM

open that folder and make another named qemu
download [http://www.h6.dion.ne.jp/~kazuw/qemu-win/qemu-0.8.2-windows.zip](http://www.h6.dion.ne.jp/~kazuw/qemu-win/qemu-0.8.2-windows.zip) to the qemu folder, and unzip it.

in there you'll find a file called qemu-img.exe
go to start/run and type cmd
cd Desktop\UbuntuVM\qemu
qemu-img.exe create -f vmdk Ubuntu.vmdk 10G  
(10G is the size of the virtual disk, it starts very small, around 1M, but but never grow above the 10G limit set here)

Copy this over this new Ubuntu.vmdk file to your main UbuntuVM folder

open up notepad and slap this in there:
```

config.version = "8"

virtualHW.version = "3"

ide0:0.present = "TRUE"

ide0:0.filename = "Ubuntu.vmdk"

memsize = "512"

MemAllowAutoScaleDown = "FALSE"

ide1:0.present = "TRUE"

ide1:0.fileName = "ubuntu-6.10-desktop-i386.iso"

ide1:0.deviceType = "cdrom-image"

ide1:0.autodetect = "TRUE"

ide1:0.startConnected = "TRUE"

floppy0.present = "FALSE"

ethernet0.present = "TRUE"

usb.present = "TRUE"

sound.present = "TRUE"

sound.virtualDev = "es1371"

displayName = "Ubuntu DeskTop"

guestOS = "ubuntu"

nvram = "Ubuntu.nvram"

MemTrimRate = "-1"

ide0:0.redo = ""

ethernet0.addressType = "generated"

tools.syncTime = "TRUE"

uuid.action = "create"

checkpoint.vmState = ""

svga.maxWidth = "1280"

svga.maxHeight = "1024"


```

Change the name of the iso file set in (ide1:0.fileName =) to whatever yours is called.

Save this file as Ubuntu.vmx in your UbuntuVM folder

If you still have your iso file, put it in this folder as well. 

If not change:
ide1:0.fileName = "ubuntu-6.10-desktop-i386.iso"
ide1:0.deviceType = "cdrom-image"

to 
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "cdrom-raw"

And put the Ubuntu install cd in your drive. 

So, at this point you should have 2 to 3 files in this UbuntuVM folder (Ubuntu.vmx, Ubuntu,vmdk, and maybe your ubuntu iso file.)

Fire up VMWare Player and select the Ubuntu.vmx file and open it. It should start up the Ubuntu installer and away you go.

Now after installing, you can get al your updates and install vmware tools to get higher resolutions and faster performance.

NOTE: I do have a VMWare server in my house, but find installing Linux distros using this method is faster for me. And you can also do this in Linux for installing Windows VM's.

---

### Post by cmost on 2007-01-19
Wow!  Before you do all that stuff that other guy suggested, edit your Xorg.conf and ensure the built in AIGLX is disabled.  You can't use 3D desktop in VMware anyway.  :-)  That may speed up your desktop considerably.

---

### Post by Hanzerik on 2007-01-19
But why have vmware server installed on a single user disktop. Vmware player, I think, works better for running multiple OS's at time on a desktop then server does. And with server you have to use the server console, vnc, or rpd to connect to it. With player you just start it up and your running your selected os.

I can run WinXP Pro, with Ubuntu, Slackware, and Debian stable VM's running all at the same time with very little performance hit. I have 2G ram and allocate 512 to each VM.

---

