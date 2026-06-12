---
title: "cannot allocate resource error"
date: 2008-05-24
forum: General Help
---

### Post by Kev192 on 2008-05-24
Hi, I am new to using Ubuntu and am having porblems after installing 7.10 on my laptop. When boot I get the screen with options for Ubuntu and windows as I am still dual booting at this point. Once I have selected to boot Ubuntu I get 2 errors:

PCI: cannot allocate resource 7 of bridge 0000.00.04.0
and
PCI: cannot allocate resource 8 of bridge 0000.00.04.0

After this the screen goes blank and there is no more information

Don't know what the issue could be as as I say I am a new Ubuntu user. Any help that you more experienced users can give would be great.

Kev

---

### Post by omababy on 2008-05-24
Sounds to me like it's a driver problem, is your laptop very new? I'd recommend installing 8.04 over 7.10 as the kernel will have newer drivers available to it. If you're willing to troubleshoot 7.10 maybe see if you can boot into init 1 by editing the kernel arguments in grub ("e" for edit at grub splash screen and add "1" to the kernel args.) and run a update "sudo apt-get upgrade" or maybe gather more info on which is the offending hardware with the lspci command and troubleshoot that way.

---

### Post by TeoBigusGeekus on 2008-05-24
The problem could be in your grub loader specification file.
Boot up with a live cd, open a terminal and post us the output of 
```
sudo fdisk -l
```
(-L)
Also, try to locate your menu.lst file. It is located in
/boot/grub/
Now, when you will have booted with the live cd, you have to find the File System partition in your Ubuntu volume. That's where the above mentioned location will be. When you will have the full path of the /boot/grub/ folder (i.e. /sdb1/boot/grub or /sda1/boot/grub etc.) type this in a terminal and post us the output
```
gksudo gedit /sbd1(orwhatever)/boot/grub/menu.lst
```

If this all seems too complicated, a fresh install would be the best choice (preferably with 8.04 this time). But before you install, make sure you check the integrity of the cd you are using (it is an option after bootup).

I hope the post helped you...

---

### Post by Kev192 on 2008-05-24
My laptop is about 2 years old. I may try 8.04 to see if that performs better than 7.10. I'll try what you have suggested and see if I can get any info but I make no promises :).

---

### Post by omababy on 2008-05-24
I'm no kernel programmer but I'd say it'd be the pci bridge itself not initializing itself properly rather than a device on the pci bus and this could be blocking data across the pci bridge.

---

