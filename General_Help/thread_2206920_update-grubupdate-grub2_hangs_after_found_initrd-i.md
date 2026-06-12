---
title: "update-grub/update-grub2 hangs after found initrd-image: /boot/initrd.img-3.11.0-12"
date: 2014-02-21
forum: General Help
---

### Post by Samarions on 2014-02-21
On Ubuntu 13.10, I tried updating grub and grub2 yesterday but only got as far as: (swedish)

```

Hittade linux-avbildning: /boot/vmlinuz-3.11.0-17-generic 
Hittade initrd-avbildning: /boot/initrd.img-3.11.0-17-generic
Hittade linux-avbildning: /boot/vmlinuz-3.11.0-15-generic
Hittade initrd-avbildning: /boot/initrd.img-3.11.0-15-generic
Hittade linux-avbildning: /boot/vmlinuz-3.11.0-12-generic
Hittade initrd-avbildning: /boot/initrd.img-3.11.0-12-generic 

```

which means something like this.  
....
found initrd-image: /boot/initrd.img-3.11.0-12-generic

current kernel: 

```

:~$ uname -a
Linux me-ESPRIMO-P510 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:52:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```



I've tried numerous things to fix this. Including following this instruction ([http://peniwize.wordpress.com/2013/12/18/how-to-re-install-all-packages-on-ubuntu/]("http://(http://peniwize.wordpress.com/2013/12/18/how-to-re-install-all-packages-on-ubuntu/)")) to find corrupted packages. And the package linux.image-3.11.0-12-generic is indeed corrupted. But to reinstall it, apt-get wants to configure grub which leads to the same freeze as the update. 

Boot repair gets stuck at os prober. 

I'm not great at this stuff, more known to mess up everything even more :/ so please help!

---

### Post by oldfred on 2014-02-21
If you are using -17, can you just delete/purge -12? We normally suggest regular housecleaning of old kernels anyway. I normally keep my working one and one older one just in case something odd happens to my working one.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

I use synaptic, but you also can use command line to remove linux images.

 In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.5.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.5.0-{17,18,19,21,22,23,24}-generic

---

### Post by Samarions on 2014-02-26
Thanks for the reply oldfred :)

since apt-get purge didn't work (it kept wanting to configure grub, which, of course, didn't work). I deleted the old kernel with synaptic instead. 

```
Hittade linux-avbildning: /boot/vmlinuz-3.11.0-17-generic 
Hittade initrd-avbildning: /boot/initrd.img-3.11.0-17-generic
Hittade linux-avbildning: /boot/vmlinuz-3.11.0-15-generic
Hittade initrd-avbildning: /boot/initrd.img-3.11.0-15-generic
```

Eventually I disabled os-prober in the grub configuration file and now I can update grub. So I guess, it's actually os-prober that is broken (therefore boot repair still doesn't work). 
Not sure where to go from here though...

---

### Post by oldfred on 2014-02-26
I have a lot of test installs and have not housecleaned many old installs on my larger drive. So os-prober takes forever to find them all. So I turn off os-prober and add my own entries into 40_custom for the few I may want to boot.

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
       Configuring the Boot Menu in Ubuntu - Boot Order in grub
[http://www.psychocats.net/ubuntu/bootmenu](http://www.psychocats.net/ubuntu/bootmenu)
[https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries](https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries)

   Ubuntu Community Documentation site
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Multiboot Ubuntu edit host names for better grub2 menu titles
[http://members.iinet.net/~herman546/p20/GRUB2](http://members.iinet.net/~herman546/p20/GRUB2) How To OS Hostnames.html

   Link with several of links below:
How to edit bootloader? Feb 2011
[http://ubuntuforums.org/showthread.php?t=1694681](http://ubuntuforums.org/showthread.php?t=1694681)

   How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

If it is os-prober and not some file it is trying to read, you can with Boot-Repair or manually totally uninstall grub2 and reinstall it.
Make sure Internet is working as you have to be able to download new copy of grub2.
 # uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda

---

