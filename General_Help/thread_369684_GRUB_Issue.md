---
title: "GRUB Issue"
date: 2007-02-24
forum: General Help
---

### Post by serion on 2007-02-24
Hello,

I have an Asus P5B motherboard with both my CD drive and my HDD connected through the jmicron PATA controller.  I have tried installing both Edgy and FC6, and both install fine, recognizing my hard drive and CD drive.  

Once the install is finished, and I reboot, GRUB drops me into the grub shell.  Anything I do in the shell gives me "Error 21: Selected disk does not exist."  The liveCDs and the windows bootloader work fine, but anytime I try using GRUB it tells me it cannot find the disk.

I have changed my bios settings to AHCI and back to IDE, and nothing has changed.  I am beginning to think I will never see my beloved Linux again :(

Thanks

---

### Post by wireddad on 2007-02-24
Have you try reinstalling Grub?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29)

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by dcstar on 2007-02-24
> **serion said:**
> Hello,

I have an Asus P5B motherboard with both my CD drive and my HDD connected through the jmicron PATA controller.  I have tried installing both Edgy and FC6, and both install fine, recognizing my hard drive and CD drive.  

Once the install is finished, and I reboot, GRUB drops me into the grub shell.  Anything I do in the shell gives me "Error 21: Selected disk does not exist."  The liveCDs and the windows bootloader work fine, but anytime I try using GRUB it tells me it cannot find the disk.

I have changed my bios settings to AHCI and back to IDE, and nothing has changed.  I am beginning to think I will never see my beloved Linux again :(

Thanks

Boot off the Live CD, mount your hard drive partition where you have installed Ubuntu and find the Grub /boot/grub/menu.lst file, open it for editing and then find the section that looks similar to this:
```
title		Ubuntu, kernel 2.6.17-11-generic
root		(**hd0,3**)
kernel		/boot/vmlinuz-2.6.17-11-generic root=**/dev/hda4** ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
```

In this example, my Ubuntu boot partition is the 4th partition (hd 0,**3**) on my first HD (**hd 0**,3) and is booting off **/dev/hda4**

Your install may have got this wrong, when your PC boots the install drive may actually be hd1 instead of hd0, and the /dev/hd designation may also be different.

Try changing the various settings and see if you can get further (back up the original file first).

BTW, does this system have SATA hardware (even if there are no drives connected)? If it does, I can imagine the install process not totally ignoring that hardware and this could cause issues later with things.

---

### Post by serion on 2007-02-25
Quick update:  Using a super grub disk floppy also gave me the same shell.  I was under the impression it was supposed to be somewhat automatic, which indicates to me that my grub install is good, there is something else incompatible.

I am currently trying to change whatever setting there are on the .lst files, and will update again soon.

---

### Post by serion on 2007-02-25
Ok looking at my menu.lst I see that:
hda3 is my /boot partition
the grub root is set to (hd0,2) which I assume is the same drive.
for the linux entry it has "root (hd0,2), kernel ..., initrd ..."
for the windows entry it has "rootnoverify (hd0,0), chainloader +1"

I only have the one hard drive, so hd0 should be correct, yes?
I cannot see anthing wrong with the way GRUB is configured.

EDIT
my device.map file looks like this:
"(hd0)        /dev/hde"

This worries me.  To mount the drive on which I found menu.lst, I used /dev/hda3.  Thin this could be it?  Should I change my device.map file?

EDIT 2
i changed device.map to
"(hd0)      /dev/hda1"
and rebooted, but I got the same error as before.  Do I have to do anything to make grub aware of the changed device.map?

Also, within the shell on the liveCD I ran 
-----------------------
>grub
grub> device (hd0) /dev/hda
and it returned 
Error 15: File not found
-----------------------
I KNOW that /dev/hda exits, I mounted /dev/hda3 in order to see the menu.lst file on my /boot partition.  What is going on here?

---

### Post by Herman on 2007-02-25
Hello serion, 
Would you like to try installing Grub in your SuperGrubDisk floppy?
```
sudo grub
``````
grub> find /boot/grub/menu.lst
``````
grub> root (fd0)
``````
grub> setup (fd0)
``` That should fix your Super Grub Floppy Disk.


If you need any specific help, can you post the output from 'sudo fdisk -lu' here please?
```
sudo fdisk -lu
```Regards, Herman

---

### Post by serion on 2007-02-25
Thanks.  Do I run the "sudo fdisk -lu" off the livecd?  

Also, I don't think anything is wrong with GRUB on the disk other than that it is trying to read off a hard drive that doesn't exist.  Is there a way to change the disk's menu.lst and device.map?

I am pretty sure thats where the problem lies, and none of the resources I can find about device.map and the way it interacts with menu.lst are very helpful.  Specifically, I need to know how to make device.map point to dev/hda instead of dev/hde, and how to make sure menu.lst registers that change for the next boot.

Thanks again.

---

### Post by Herman on 2007-02-25
Yes, you can run 'sudo fdisk -lu' from a terminal in the LiveCD.

You can also mount your hard disk installed Ubuntu filesystem and access your /boot/grub/menu.lst file from the LiveCD. This link will tell you how,                              [Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")

In most cases a little simple editing in the menu.lst file is all that is necessary to cure most common booting problems. 
If you have IDE and SCSI (SATA) drives connected in the same computer you might want to edit the device.map file and re-install grub, but that is not so often needed.

Regards, Herman :)

---

### Post by serion on 2007-02-26
So, if I edit the device.map file, I have to re-install grub?  I think thats going to be my next step, but I'd like to know what it involves.  Thanks

---

### Post by Herman on 2007-02-26
I haven't had the need to edit grub's device map yet myself, so the only way I can find out about it is by reading about it. I'm not running any computers that are that complicated. I assembled one that can take two SATA disks and four IDEs but I haven't got it running yet. Not long ago another user solved booting problems by editing the device.map file, I added it to my Grub web page, here's the link, [**Editing Grub's device.map** (when you have SATA and IDE hard disk drives in the same machine, and Grub won't boot anything]("http://users.bigpond.net.au/hermanzone/p15.htm#device.map")

Regards, Herman :)

---

### Post by serion on 2007-02-26
So I reinstalled and tried again (and again and again) and nothing seems to work.  The super grub disk was able to load stage 2 and get me as far the the "grub>" prompt, but I could not set the root to hd0.  Loading from drisk, grub got as far as "loading stage 1.5, loading please wait, error 21."  At this point i did not even get the grub> prompt, but a blinking "_".  

So far I have edited my device.map (which was correctly pointed at dev/hda this time anyway), edited my menu.lst, and changed BIOS settings.  What else is there to explain grub's inability to find my hard drives?

---

### Post by Herman on 2007-02-26
If you need any specific help, can you post the output from 'sudo fdisk -lu' here please? ```
sudo fdisk -lu 
```and also a copy of the bottom part of your /boot/grub/menu.lst file too? ```
sudo gedit /boot/grub/menu.lst
```Thank you,Regards, Herman :)

---

### Post by Herman on 2007-02-26
> The super grub disk was able to load stage 2 and get me as far the the "grub>" prompt, but I could not set the root to hd0. Or, if you prefer, you can probably solve the problem yourself as long as you have the grub>_ prompt.
See how to use grub to investigate your computer and boot it up manualy from the grub prompt in this link,  [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
Actually, you should be able to solve your problem that way very quickly and easily once you try some of those tips and ideas.

Regards, Herman :)

---

