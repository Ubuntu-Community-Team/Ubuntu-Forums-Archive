---
title: "What software to use for making a booting USB ?"
date: 2021-09-24
forum: General Help
---

### Post by oden99 on 2021-09-24
I am trying to make some booting USB's of some .iso files "NOT ubuntu"
Just other .iso files.

I tried the "Startup disk creator but that one only seems to create Ubuntu USB's and can not burn any other files of .iso type.

If  I try to load a .iso in the "Start up disk creator". the software refuse to load and display the .Iso choosen.
And it will not burn to the USB.

What kind of software is there to use ? for "burning" an .iso file to USB in Ubuntu ?
Do I really have to load windows for a simple task like burning an .iso ?

Most search links only describe how to burn an installation ubuntu booting USB.. Not any iso to USB.

'
I tried with AROS disks. like Ikaros Live and Morph os  and others but with the same result.

---

### Post by Holger_Gehrke on 2021-09-24
If you want a tool with a graphical UI then either Balena Etcher will work. Otherwise dd can do it. Something like
```

sudo dd if=path_and_name_of_iso_file of=/dev/device_file_for_usb_flash_drive bs=16M status=progress

```

Just be careful to get the device file right, dd will write where you tell it to and will not warn you if you're doing something horribly bad like overwriting your boot device.

Holger

---

### Post by grahammechanical on 2021-09-24
I had the same problem when I wanted a bootable USB of Debian. I installed mkusb and it had no problem making bootable USB sticks of several different ISO images

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Regards

---

### Post by yancek on 2021-09-24
In addition to those tools suggested, others which may work are unetbootin, universal usb installer and ventoy.  If you have a Linux OS installed, the dd method is simple and reliable and mkusb is excellent if using Ubuntu.

---

### Post by TheFu on 2021-09-24
I used to use **unetbootin**, then **yumi**, then **dd**, then **ddrescue**.  They were all too complicated.

These days I use cp.  Yes, cp.  Any command that can move bits, unmolested, from A --> B can be used.
So, taking an example from above:
> sudo dd if=path_and_name_of_iso_file of=/dev/device_file_for_usb_flash_drive bs=16M status=progress
I'd use 
```
sudo cp path_and_name_of_iso_file /dev/device_file_for_usb_flash_drive
```
A real example on my system is:
```
sudo cp /raid/media/VMs/ISO/ubuntu-20.04.3-live-server-amd64.iso /dev/sdk
```
It is crazy simple. Been using it over a year now. Never had any issues, though normal USB flash drive problems can happen.  It also works with SDHC, so if you have a laptop that can boot from an SDHC slot, that works too.

Played with **mkusb** about 5 times last summer. Found it too complicated.  Tried etcher - could anything be so bloated?  Felt like iTunes all over again.

Of course, the ISO must be bootable. That's in the build of the ISO, not in the bit-for-bit copy.  Not all ISOs are bootable, so none of these methods will magically create a bootable system if it wasn't built that way already during the ISO creation.

If you don't want to use **cp**, you can use **cat** with redirection too.  sudo (cat input.iso > output-device)  - I think that will work.

---

