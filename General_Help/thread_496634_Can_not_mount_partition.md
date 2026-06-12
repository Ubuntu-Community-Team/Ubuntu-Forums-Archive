---
title: "Can not mount partition"
date: 2007-07-09
forum: General Help
---

### Post by puudutus on 2007-07-09
Ok, here's the story  :( . I use a dual boot system running Suse 10.2 64bit and Ubuntu 7.04 32bit.
Both systems were working fine until I tried to configure my MX500 mouse to work properly in Ubuntu  (I had it working in Suse before). When I edited my xorg.conf file something must have gone wrong.. ubuntu didn't boot anymore :blink: . I booted Suse and tried mounting the partition where Ubuntu is installed so I could fix my mistake... I seriously messed up something because the next time I tried to boot Grub gave me an error 17. Couldn't get grub to boot from the partition it used to boot from but managed to get it to boot from the Suse partition. I am at lost.. I have lott's of stuff I really need on the Ubuntu partition (dev/hda3).. like logos and web pages...

Suse is working fine.

My question is how can I access the data on hda3 ? (I don't need to save the ubuntu installation, but I really need the data on the disk)

Here's a screen shot from my [partition table](http://www.emuri.fi/samuli/partitions.jpg):

[img]http://www.emuri.fi/samuli/partitions.jpg[/img]

I tried the command "*mount /dev/hda3 /media/ubuntu*"

which gives me a result:

[i]linux:/home/samuli # mount /dev/hda3 /media/ubuntu
mount: unknown filesystem type 'LVM2_member'
linux:/home/samuli # [/i]


Not very experienced whit Linux.. but I trust there is some way to make this work. Can anyone help me whit this problem?

I have tried the ubuntu live-cd whit no luck

---

### Post by jeff0149 on 2007-07-09
I am new to Linux myself.  I can understand wanting to look at a couple of versions (Suse and Ubuntu), but I don't get why you want to run both.  I have found that even in Linux software some developers specify Gnome, Debian or some other things.

Linux installs very easy and I had to reload a second time to make the partitions work.  I may have to reinstall again unless I can figure how to unmount the same partition you mentioned.

My advice, and it is worth what you pay for it, is pick a version of Linux you want to run and install that one.  I previously needed to have two copies of Windows XP on my laptop due to a crash and then reformatted the drive.  I think the same may be necessary here.  If you are storing any needed information on you Linux computer, back it up on a CD-ROM or other removable media until you are comfortable with the Linux system and your knowledge of it.
Jg0149

---

### Post by puudutus on 2007-07-09
The problem isn't having 2 versions of linux.. the problem is I can't access the data on the LVM partition..

The reason I use both Suse and Ubuntu is that Suse supports my hardware better.. Ubuntu I like cause for the most it it's easier to use (installing the apps I need and keeping them updated also seems to work better). And I want to learn how to use more than one distro..

---

