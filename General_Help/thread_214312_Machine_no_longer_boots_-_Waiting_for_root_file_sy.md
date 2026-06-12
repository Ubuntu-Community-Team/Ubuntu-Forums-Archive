---
title: "Machine no longer boots - Waiting for root file system..."
date: 2006-07-12
forum: General Help
---

### Post by msemtd on 2006-07-12
I did a kernel upgrade on Sunday and the machine no longer boots. It hangs following the message "Waiting for root file system..." 

There's similar posts on the forums and I think I've read them all, but none of the suggestions have worked. WTF is going on?

](*,) 

BTW: the machine is the MAME cabinet for LugRadio Live - we need a fix quick!

---

### Post by tozebr on 2006-07-22
i am having the same problem, trying to update to 2.6.17 it ahng up on waiting for root file system. after 5 min it shows:
/dev/sda doesn´t exist!
dropping to a shell


how can i fix it?

on my older kernel i boot normaly

---

### Post by justinchudgar on 2006-08-18
I'm having the same problems. Tried an apt-get dist-upgrade and everything seemed to go smoothly. On reboot, though, I cannot get into either the 2.6.15.? or the 2.6.17.8 kernel in either normal or recovery modes. Every try leads to a boot screen showing "Waiting for root file system".

I've had this happen on both a VMWare guest install and on a direct install, albeit a dual boot box with XP.

---

### Post by djsamsel on 2006-08-19
i've had the same problem for awhile. you can track you problem a little further by doing a safe boot and seeing what line of code you hang on. that will give the true linux geeks the ability to help you further. when you get the line, you can also search google for what linux is doing atm, and possible track down the offending piece of hardware (in my case it was the firewire ports). hope this helps you take the next step.

---

### Post by kondr on 2006-09-22
I faced the same problem on my gentoo server. Moreover, common upgrade procedure (aptitude - u - select all upgradable packages - g - g) was Ok on my workstation (in a minute I managed to boot into 2.6.17 kernel) and lead to the same error ("Waiting for root file system...") on my server.

The solution was as follows. I booted the server from gentoo rescue CD, mounted my / partition and edited the /boot/grub/menu.lst file. On my workstation, I had an IDE HDD, on the server - an SATA one, but after the upgrade for unknown reason I found only "/dev/hdc1" devices in the /boot/grub/menu.lst file. That was Ok for 2.4.27 kernel (yes, I managed to boot into 2.4.27 kernel on the server right after the upgrade), but to boot into 2.6.XX kernel you should sed s/hdc1/sda1/. Do not change the lines describing the 2.4.27 boot sequence.

After that, I had no problems booting into 2.6.XX kernels on my server.

---

### Post by CanOfMDAmp on 2006-10-01
I too have the same problem, but for some reason cannot find the /boot/grub/menu.lst file to fix it.

Any ideas?

EDIT: Oops, I was stupid. I looked in the wrong place (using a live distro, and getting two of my monitors confused.)

---

### Post by zergberg on 2006-10-01
My experience with this error had to do more with my motherboard's poor quality manual, but I guess the concept is the same. Anyway, find a liveCD with GParted and see if hda and hdb have magically become hdc and hdd. If they have, it's a simple matter of editing /etc/fstab. Otherwise, I have no idea.

---

### Post by bastupungen on 2006-10-01
I got this problem while adding more hdd's and sata card. I fixed it by randomly testing other drive names in the grub boot menu (press e to edit, i think) 

Also something that might be interesting. For some reason when i upgraded my kernel some of my hdd's got called /dev/evms/sd*.. might help might not. But I would really like to know why my hdd's suddenly changed name, accually, quite irritating.

---

### Post by SonicSteve on 2006-10-03
Hi Guys,
By the sounds of this is doesn't sound like you have the same the issue as me, but the I got the same error.
Mine was caused by installing Ubuntu while the hard drive was on IDE2 (secondary)instead of IDE1 (primary). So I switched them and found that I couldn't boot after doing it. 
So I switched them back and now I'm running smoothly again. I will try to learn how to switch the FStab file to recognize the file system on IDE1 but for now this worked.

---

### Post by govedarov on 2006-10-15
I have the same problem too. It says waiting for root file system and then stalls, then drops into a shell and doesn`t wanna start. The fun part is that I have older kernel as well ( the one from the breezy install yesterday), and I can boot from it, but it loads almost no modules. 

Here is my grub file :

> # ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-k7
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-k7 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-27-k7
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.12-9-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


As you see, all 3 kernels use the same device /dev/sda2 and with the old kernel it works - with the other 2 - no. 
Can anyone tell me how to solve this?

---

### Post by kondr on 2006-10-16
The problem looks different from mine.

Anyway, here are some ideas.

1) You should use either 386 or k7 kernel. You can boot some 386 kernel (2.6.12), so delete first two blocks from the /boot/grub/menu/lst file and leave only 5 (386 kernels and memtest).

2) Maybe the problem is due to the change hotplug/udev (2.6.12 kernel worked with hotplug only, 2.6.15 kernel works with udev only). So, for 2.6.15 you should do the following:
aptitude purge hotplug; aptitude install udev
Some info is available in Wiki: [http://en.wikipedia.org/wiki/Udev](http://en.wikipedia.org/wiki/Udev)

3) In the /boot/grub/menu.lst file several comment lines in the beginning are used for grub upgrades. Please edit the lines
# kopt=root=/dev/hdc1 ro
# groot=(hd0,0)
etc (some explanations could be found in the beginning of this file).

4) I've found it's a good idea to store an external copy of /boot/grub/menu.lst, /etc/fstab files to check if something changed (btw, do these files use identical device names now)?

In case nothing helps please post more info (whole /boot/grub/menu.lst and /etc/fstab files; dmesg info; what devices do you see while booting from a resque CD; HDD type - IDE, SATA, SCSI; lsmod; what kind of upgrade broke the things).

Regards, Vladimir

---

### Post by pablohoffman on 2006-11-25
i also had this problem and fixed it by rebuilding the initramfs for the problematic kernel.

update-initramfs -k 2.6.17-10-generic -c

(change 2.6.17-10-generic to suit your kernel version)

---

### Post by Khisanth on 2006-12-13
Can you all check /proc/cmdline and see what it shows?

I had an MD RAID1 / LVM install on i386 as well as AMD64 and after installing Edgy 6.10, I could never get my machine to boot up after the install.

Turns out for some reason GRUB was sending a whole lot of garbage to the kernel commandline.

cat /proc/cmdline gave me
EEEEEEEEEEEEEEEEEE and some non-english characters as well.

I installed LILO and had to do some manual tweaking of /target/etc/lilo.conf before I got my machine to boot.

---

### Post by beatshoes on 2007-04-25
ya hoo! this did the trick for me too,
after downloading the edgy dvd and installing, not more than a day later feisty arrives, updated, wouldnt boot the kernel 2.6.20-15-386, after booting a generic kernel i was able to get something a little more functional.

after reading several posts from both ubuntu issues and debian issues all pointing to removing udev or hotplug,
i began to attempt to remove udev, bleh! it then wanted to remove just about all of gnome because of some dependancy issues.... i decided this was possibly not a good idea, and went in search for a better option. 
and yep! update-initramfs -k 2.6.17-10-generic -c solved it.

what an awesome introduction to linux, after being a pc tech for windows, ubuntu is a joy to fix.
thanks for your help pablohoffman

---

### Post by apricot on 2007-05-18
I solved the problem of waiting for root file system. The problem arised when i changed my graphic card. Ubuntu changed partition names from hda to hdc, so i modificated /boot/grub/menu.lst line:

kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda7
to:
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc7

and i also modificated /etc/fstab on points where hda appears i changed it to hdc.
If you have mounted partitons, leave only names of the directory in /etc/fstab like they was:
example:
/dev/hdc5       /media/**hda5**     vfat    defaults,utf8,umask=007,gid=46 0       1

Also, i do not know what changed, but my Ubuntu partition was on hda3, and now is on hdc7.
You can verify on which partition Ubuntu is by running gparted on Ubuntu Live CD.

That's all.

---

### Post by apricot on 2007-05-20
Pardon, the problem occured due to kernel upgrade, but it all works now, how i explained in previous post!

---

### Post by apricot on 2007-05-20
To modificate files you need use Ubuntu Live CD and mount the partition with command:

mount /dev/hdx

Change x with the number of Ubuntu partition. You can check it by entering:

sudo gparted 

in the terminal.

---

### Post by apricot on 2007-05-20
Me again. The problem occured due to change of IDE cabel of the hard disk and the cd-rom.

---

### Post by sefmars on 2007-11-15
I had the same problem after a kernel upgrade , the thing was theat hda1, hda2.. etc became hdb1,hdb2...

The most simple fix is: you boot with a bootable cd into a shel then:

```
fdisk -l
```

you should see your partition label

then reboot press e at boot sequence , modify the root file sistem,you shold be able to boot like this , then modify 

/etc/fstab

and

/boot/grub/menu.lst


with the new partition  label

---

