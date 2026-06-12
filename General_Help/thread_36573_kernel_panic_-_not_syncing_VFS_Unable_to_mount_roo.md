---
title: "kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"
date: 2005-05-23
forum: General Help
---

### Post by DarkSilver on 2005-05-23
Hello,

There is the same problem in Breezy, but I am with **HOARY**!

after dist-upgrading my hoary (hoary-security is in my sources.list)
I have a new kernel : [http://www.ubuntuforums.org/showthread.php?t=36375](http://www.ubuntuforums.org/showthread.php?t=36375)

but, when I boot :
**kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)**
 

when the installation, i have something like this :
cpio: (0xfffe000) : no such file or directory
 cpio: /lib/ld-linux.so.2 (0xb7feb000) no such file or directory


The 2 posts in the Breezy forums hasn't any solution...
Do you know how I can resolve it ??

- boot from LiveCD and chroot to /dev/hda1? and then? what can I do ?


thanks !

---

### Post by jobezone on 2005-05-23
I have this exact same problem, upgraded using only the oficial hoary repositories, to linux 2.6.10-5-686 . I guess it-s a bug in the kernel? In the past, whenever I upgraded to a new linux version, I kept the old one, and added an entry for it in Grub, just in case. But not this time, I figured it would be ok...

---

### Post by benplaut on 2005-05-23
good! it's not just me!

but what to do until it's fixed? how can i gte GRUB to boot into the old kernel? anyone?

---

### Post by wd3 on 2005-05-24
I've upgraded "initrd-tools" to breezy version, and the problem gone.

initrd-tools : 0.1.78ubuntu1

---

### Post by benplaut on 2005-05-24
[QUOTE=wd3]I've upgraded "initrd-tools" to breezy version, and the problem gone.

initrd-tools : 0.1.78ubuntu1[/QUOTE]

how do you update without booting into your system? is it possible from LiveCD?  :|

<<UPDATE>>

OK, i added the breezy repos to the end of my sources.list, and (while in chroot) apt-get update. After it took forever to find the repos, it didn't have any failures for the breezy repos. I apt-get install initrd-tools, and it told me that it was upgrading (to the correct version), and it installed. I rebooted, and, ...


 \\:D/ 





















 \\:D/ 



















same thing happens  ](*,)  ](*,)

---

### Post by DarkSilver on 2005-05-24
argh benplaut ....
When I was reading your post it seems it was ok.... but no...
false hopes :?

so nobody have a solution ?

just for information:
to do a chroot from the LiveCD, you only need to do : sudo chroot /dev/hda1 /bin/bash ?

but then, what can I do ?

---

### Post by jobezone on 2005-05-24
[QUOTE=benplaut]how do you update without booting into your system? is it possible from LiveCD?  :|

<<UPDATE>>

OK, i added the breezy repos to the end of my sources.list, and (while in chroot) apt-get update. After it took forever to find the repos, it didn't have any failures for the breezy repos. I apt-get install initrd-tools, and it told me that it was upgrading (to the correct version), and it installed. I rebooted, and, ...


 \\:D/ 





















 \\:D/ 



















same thing happens  ](*,)  ](*,)[/QUOTE]
 benplaut:

good that you can keep the spirits up!!:) actually, you made me laugh:))

I'm thinking of backing up my home dir to the fat partition, and reinstalling.

---

### Post by benplaut on 2005-05-24
[QUOTE=DarkSilver]argh benplaut ....
When I was reading your post it seems it was ok.... but no...
false hopes :?

so nobody have a solution ?

just for information:
to do a chroot from the LiveCD, you only need to do : sudo chroot /dev/hda1 /bin/bash ?

but then, what can I do ?[/QUOTE]

OK, i figured it out!  \\:D/  (for real this time)

here's how to boot into hoary:

get a Distro that has a bootloader built in. I used SuSE 9.2 (manual installation, enter, enter, boot installed system, enter)

You will get tons of errors on boot, but don't worry. Log in.
(BTW, if this seems confusing, just ask)

Open up a terminal (or ctrl-alt-F1), put in the hoary install CD, and type:

```
sudo apt-cdrom add
```

Wait until it finishes, and then open up synaptic (if you typed ctrl-alt-F1 to get to the terminal, type ctrl-alt-F7 to get back to Gnome)

Search for "linux-image-2.6.10-5-386"... this won't work for the i686 kernel... sorry  :neutral: , and press ctrl-e. Select, in the box "2.6.10-34 Hoary"... _not_ 2.6.10-34.1

press OK, and then Apply. Note: you have to still have the Hoary CD in the drive... network connections probably won't work

After it's done, take out the disk and reboot. When GRUB is loading, press ESC and confirm that it is booting from the i386 standard image. 

A few seconds later, when the system *hopefully* boots correctly, open up Synaptic, and find the same package (linux-image-2.6.10-5-386) again. Select it, go to the "Package" menu (at the top of the screen), and select "Lock Version". This will stop the update manager from bugging you to update to the buggy version (undo this when a non-buggy kernel is released).

There are some problems with this method... most notably that the Network Applet does not work properly afterwords... but i'm working on it  O:) 

Enjoy!

---

### Post by Michal Fapso on 2005-05-25
Hello,

I had the same problem with upgrading linux-image. Then I booted from ubuntu-live, mounted the hdd linux partition, chrooted, 

```

mount /dev/hda7 /mnt/linux
chroot /mnt/linux /bin/bash
mount -t proc /proc /proc
apt-get install linux-image-2.6.11-1-386

```

...and it works  :grin: 

Maybe it is not needed to upgrade to kernel 2.6.11-1, but this is how it worked for me

Good luck

---

### Post by benplaut on 2005-05-25
[QUOTE=Michal Fapso]Hello,

I had the same problem with upgrading linux-image. Then I booted from ubuntu-live, mounted the hdd linux partition, chrooted, 

```

mount /dev/hda7 /mnt/linux
chroot /mnt/linux /bin/bash
mount -t proc /proc /proc
apt-get install linux-image-2.6.11-1-386

```

...and it works  :grin: 

Maybe it is not needed to upgrade to kernel 2.6.11-1, but this is how it worked for me

Good luck[/QUOTE]


i tried 2.6.11 kernel a few months ago, and it doesn't play fair!  :-x

---

### Post by greg_mci on 2005-05-25
I get the same error.

Tried fixing it with (k)ubuntu live, also installed 2.6.11.1, but still get the same error.  ](*,)

---

### Post by Michal Fapso on 2005-05-26
Thank You for the warning, Benplaut. So here is another solution (for kernel 2.6.10-5):

Boot from ubuntu-live (or another live linux)
```

mount /dev/hda7 /mnt/linux
chroot /mnt/linux /bin/bash
sudo apt-get install initrd-tools
sudo mount -t proc /proc /proc
sudo apt-get remove linux-image-2.6.10-5-386
sudo apt-get install linux-image-2.6.10-5-386

```

initrd-tools are needed to set up the kernel image. Because I didn't have it installed before I updated my old kernel to the 2.6.10-5, the kernel setup process after downloading packages was not successful. In my case (I have nVidia card) it was needed to "sudo apt-get nvidia-glx" also (it was removed together with linux-image).

If it does not work for you, please don't forget to post also your error output

To greg_mci: have you installed initrd-tools before upgrading the kernel? Anyway try rather this solution (described above) because the 2.6.11 kernel may not be as stable as 2.6.10-5.

Never give up!

---

### Post by greg_mci on 2005-05-26
Thank you for trying to help, Michal Fapso.

When I wanted to install the initrd-tools, they were already there, and after I removed and installed the kernel again, I still got the same error...


Not only my kernel, but also me is beginning to panic. Is this the end of ubuntu?

HELP!!!  :mad:

---

### Post by gh0s1 on 2005-05-26
@greg_mci

you must DOWNGRADE following packages from hoary:

-> locales 2.3.2.ds1-20ubuntu13
-> libc6 2.3.2.ds1-20ubuntu13
-> libc6-dev 2.3.2.ds1-20ubuntu13
-> libc6-i686 2.3.2.ds1-20ubuntu13

 \\:D/   :wink:

---

### Post by greg_mci on 2005-05-26
How do I downgrade? Sorry, I'm quite a noob...

I've finished with Ubuntu anyways, am gonna install Kubuntu instead (I know, it's not  really different, and I could have updated to it).

Thank you, guys!  :razz:

---

### Post by cutOff on 2005-05-26
[QUOTE=benplaut]i tried 2.6.11 kernel a few months ago, and it doesn't play fair!  :-x[/QUOTE]
Did you try to boot by adding 'inotify' option to the kernel boot parameters??

It seems to be an incompatibility between reiserfs+dbus+inotify.

---

### Post by jobezone on 2005-05-26
Well, I baked up my home dir, and reinstalled. Upgraded the kernel, but made sure I kept the one Hoary CD had, but the new one worked. I still don't understand what happened, and it was quite sad that I had to do this. I started using ubuntu since october last year, and never had to do a reinstall.

---

### Post by rejser on 2005-05-26
I had this problem when I kept my old fstab from older system. 
Never thought that it could be the fstab file, but it was.

---

### Post by apis on 2005-05-29
Ok guys. 

I had the same issue and all above mentioned solutions didn't work with me. So here is what helped me out:

Take Live CD, boot

```
mount /dev/hda7 /mnt/linux
chroot /mnt/linux /bin/bash
sudo mount -t proc /proc /proc
**sudo apt-get install binutils**
sudo apt-get install --reinstall linux-image-2.6.10-5-386
```
Reboot and enjoy  :) 

Basically you should upgrade binutils to version 2.15-5ubuntu2.2 and after that reinstall kernel. It should solve that issue with:

```
cpio: (0xfffe000) : no such file or directory
cpio: /lib/ld-linux.so.2 (0xb7feb000) no such file or directory

```
Since in that version was fixed something related to ld:

> It was discovered that the packages from USN-136-1 had a flawed patch
with regressions that caused the ld linker to fail. The updated
packages fix this.
Anyway it worked for me  :)

---

### Post by goldenboy on 2005-06-27
What helped me out of this mess was updating the initrd-tools to the breezy version (0.1.78) as it was proposed [here](http://www.ubuntuforums.org/showthread.php?t=27709).

---

### Post by wishyjr on 2005-10-22
ok, im trying all of this as ive got a mucked up kernel it would seem. im running ubuntu from a live cd and my system is not starting the 2.6.10-5-amd64 generic kernel. again, all i was doing was using the ubuntu updater thingy- switched off-when i came back to the pc it threw the kernel panic.

im trying to run the commands posted by you guys (like i said) from the ubuntu live cd i got from work today but the first command to mount stuff isnt letting me. its saying that i need to specify the filesystem type -but where in the command, --help isnt a great deal of help either. 

Also, how can i display the partitions of my hard drive using the live cd in the terminal? im just not too sure which partition i put my ubuntu install onto.

thanks

UPDATE: worked it out, i hadnt updated my sources.list :)

---

### Post by keyshawn on 2005-12-13
Hi,

I've encountered this problem and trying to follow the steps to remedy this. 
Right now, I'm trying to upgrade my sources list. 
I was able to successfully do this by issuing the command:
sudo gedit /mnt/linux/etc/apt/sources.list

and replaced all instances of hoary with breezy [and I saved the file]. However, when I tried to sudo apt-get update, the list still had all of the hoary links in there :confused:

Do i have to issue the standard 'sudo apt-get update' command differently, since i'm doing this to a mounted drive ?

regards,
will.

PS - I'm using a hoary live cd. I ran out of blank cd's, haven't had the chance to run to the store yet.

---

### Post by ah.heng on 2006-01-14
hey guys, is it possible that this might be a hardware error?

if so, would it be the ram or the harddisk?


it's been happening quite often for me the past 3 weeks. i'll be in XP doing some stuff when the blue screen pops up. after that it auto reboots, if i boot into ubuntu, i) that error appears, ii) it runs fine for a while, then everything freezes.

if i boot into XP, it either i) reboots again almost immediately, ii) run fine for a while before another BSOD.

---

