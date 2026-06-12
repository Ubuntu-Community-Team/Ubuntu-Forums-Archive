---
title: "Kubuntu installed and now"
date: 2007-01-13
forum: General Help
---

### Post by Uturn-Zone on 2007-01-13
okay I installed kubuntu now... Edgy

#1:
I could have sworn I had a 80Gb harddrive and now got only 40GB ????????
I installed it from the live cd and choose "Erase entire disk" and I gues windows xp should be gone from my harddrive now... 

help please?

#2: 
My network worked prefectly fine on windows xp, the other pc in my p2p network is also windows xp, and now I installed it it doesn't work anymore?

Even when I shutdown Comodo Firewall on the xp computer it still won't connect:
"Limited or no connection"

I am lost here... Help me out!?

---

### Post by dbd on 2007-01-13
#1
Not sure why you only have 40Gb. Probably a good idea to have a look at the partition table to find out whats going on, see here for info:
[https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/partitions-booting.html)

#2
What are you using to try and connect? What do you want to do? You may need to install samba on the linux machine to get it to network correctly with windows.

---

### Post by Uturn-Zone on 2007-01-13
#1:
Okay I will check it out.

edit: I really don't understand that page at all.. remember I am a noob to linux/kubuntu, but not to computers...

#2:
well I want to put it on the network, that now contists of 2 xp computers and putting another one in it, this will require 2 switches.. going out of that position.. I want to share files on 1 computer which all 3 can acces and I want them all to get on the internet...

Where do I get samba from?
can I download it on an xp pc and transfer it with a usb stick to the linux (kubuntu) pc?

---

### Post by dbd on 2007-01-13
I'm assuming from your last sentence that you havn't got the internet working with kubuntu yet, so will focus on that first.

> **Uturn-Zone said:**
> #1:
Okay I will check it out.

edit: I really don't understand that page at all.. remember I am a noob to linux/kubuntu, but not to computers...

Ok, I think before looking into that we need to get the net sorted, because you need to install a new program to have a proper look at your partition table, and it is easier to install software once you have the internet set up.

For now however we can have a quick look if you open a console and run this command:
df -h
and post the output here.

> **Uturn-Zone said:**
> #2:
well I want to put it on the network, that now contists of 2 xp computers and putting another one in it, this will require 2 switches.. going out of that position.. I want to share files on 1 computer which all 3 can acces and I want them all to get on the internet...

How do you access the internet? Do your computers access it by all being connected to a router, or do they all access the net via one particular computer (does one specific computer have to be on for the others to be on the net?)

---

### Post by Uturn-Zone on 2007-01-14
sorry for my late reply

my output: 
> 
filesytem size used avail use% mounted on
/dev/hdal 36g 1.8g 125m 33g 6% /
varrun 125m 80k 125m 1% /var/run
varlock 125m 0 125m 0% /var/lock
procbususb 10m 92k 10m 1% /proc/bus/usb
udev 10m 92k 10m 1% /dev
devshm 125m 0 125m 0% /dev/shm
lrm 125m 18m 108m 14% /lib/modules/2.6.18-10/generic/violatile


dunno what it means

#2:
atm I connect with internet through my host computer (Peer to peer network) the host pc needs to be on for the other pc to go online

later on (a month orso) I will have a switch or 2 that will let all the computers go on the internet indepently

---

### Post by dbd on 2007-01-15
#1
I've just had a thought of how you can have a look at what partitions you have without any partitioning software. If you type in this command:
> ls /dev/hd*
It should give us a list of all your hard drive partitions.

Also, I'm not sure if you'll have it installed, but you could try this command:
> sudo fdisk /dev/hda
and then press p and post the output here. (After that be sure to quit using q, you don't want to be accidently pressing buttons in fdisk, you could damage your hardrive).

As for the output of df, this is what the second line means:
/dev/hda1 - the name of the partition (the first partition on the first hard drive)
36g - the size of the partition
1.8g - used space in the partition
125m - I don't know
33g - free space on the partition 
6% - percentage use of the partition
As for the other lines, I don't really know, but I do know that they are not partitions of your harddrive.

2#
I just had a look around the forums, and I think this thread should help:
[http://ubuntuforums.org/showthread.php?t=333106](http://ubuntuforums.org/showthread.php?t=333106)

---

### Post by Uturn-Zone on 2007-01-15
(note: I have installed kubuntu from live cd with windows installed and didn't saw anything about formating? is it true that kubuntu uses FAT is stead of NTFS and maybe that's the problem?, just a thought ;) )

#1:
ls /dev/hd*:
> (in yellow)
/dev/hda /dev/hda1 /dev/hda2 /dev/hda5 /dev/hdc /dev/hdd


Fdisk:
> Disk /dev.hda: 40.0GB 40...,....... bytes
255 heads, 63 sectors/tracks, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 4772 38331058+ 83 Linux
/dev/hda2 (no star) 4773 4865 747022 5 Extended
/dev/hda3 (no star) 4773 4865 746991 82 Linux swap / Solaris


#2: 
I will go take a look at that thread, thanks :P
edit: I read something about ICS.. I will go take a look at that xp machine when my sis is gone ;)
edit 2: as far as I can tell ICS is on.. and it still doesn't work... argh...

---

### Post by dbd on 2007-01-16
> **Uturn-Zone said:**
> (note: I have installed kubuntu from live cd with windows installed and didn't saw anything about formating? is it true that kubuntu uses FAT is stead of NTFS and maybe that's the problem?, just a thought ;) )
Nope, ubuntu uses the linux filesystem ext3, and would probably just have deleted your old partitions rather than formatting.
> **Uturn-Zone said:**
> 
#1:
ls /dev/hd*:
 (in yellow)
 /dev/hda /dev/hda1 /dev/hda2 /dev/hda5 /dev/hdc /dev/hdd 

Fdisk:
 Disk /dev.hda: 40.0GB 40...,....... bytes
 255 heads, 63 sectors/tracks, 4865 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 
 Device Boot Start End Blocks Id System
 /dev/hda1 * 1 4772 38331058+ 83 Linux
 /dev/hda2 (no star) 4773 4865 747022 5 Extended
 /dev/hda3 (no star) 4773 4865 746991 82 Linux swap / Solaris 

Hmm, strange Fdisk output, are you sure that was everything?
Anyway, ls /dev/hd* has shown you have two more partitions that you do not have mounted: hda2 and hda5. 
You can mount these by going into the KDE System Settings, then selecting the advanced section, and within that you want Disks & Filesystems. If you click on the button to go into administer mode then you should be able to choose to mount these partitions at particular mount points, (if your not sure where you want them then for now you might as well choose /media/hda2 and /media/hda5) (If you're not sure how then feel free to ask for a more in depth explanation). Now the rest of your free space will be accessible in these two directories.
[QUOTE=Uturn-Zone;2016716]
#2: 
I will go take a look at that thread, thanks :P
edit: I read something about ICS.. I will go take a look at that xp machine when my sis is gone ;)
edit 2: as far as I can tell ICS is on.. and it still doesn't work... argh...
Hmm, afraid I can't really help you there. If you can't find any solutions on the rest of the forum it might be worth starting a thread in the networking help forum.

---

### Post by Uturn-Zone on 2007-01-17
> **dbd said:**
> Nope, ubuntu uses the linux filesystem ext3, and would probably just have deleted your old partitions rather than formatting.
[QUOTE=Uturn-Zone;2016716]
#1:
ls /dev/hd*:
 (in yellow)
 /dev/hda /dev/hda1 /dev/hda2 /dev/hda5 /dev/hdc /dev/hdd 

Fdisk:
 Disk /dev.hda: 40.0GB 40...,....... bytes
 255 heads, 63 sectors/tracks, 4865 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 
 Device Boot Start End Blocks Id System
 /dev/hda1 * 1 4772 38331058+ 83 Linux
 /dev/hda2 (no star) 4773 4865 747022 5 Extended
 /dev/hda3 (no star) 4773 4865 746991 82 Linux swap / Solaris 

Hmm, strange Fdisk output, are you sure that was everything?
Anyway, ls /dev/hd* has shown you have two more partitions that you do not have mounted: hda2 and hda5. 
You can mount these by going into the KDE System Settings, then selecting the advanced section, and within that you want Disks & Filesystems. If you click on the button to go into administer mode then you should be able to choose to mount these partitions at particular mount points, (if your not sure where you want them then for now you might as well choose /media/hda2 and /media/hda5) (If you're not sure how then feel free to ask for a more in depth explanation). Now the rest of your free space will be accessible in these two directories.

Hmm, afraid I can't really help you there. If you can't find any solutions on the rest of the forum it might be worth starting a thread in the networking help forum.

please give me an indept explanation :)

and about the network.. I will get back to you folks with that when the current network is stable (it keeps breaking down) 
and when I have bought some hardware where I can put all 3 together :P

---

### Post by dbd on 2007-01-17
Sorry, I'm a fool, didn't really have a good look at the fdisk output the first time.
It looks like fdisk thinks your hardrive is 40Gb, and there is no missing hard drive space I'm afraid. 
I've never heard of fdisk getting something like this wrong, but I suppose it might be possible. If you want to double check you canrestart your computer and then go into the bios (press delete or F1 or escape or something, it'll tell you when the computer first boots) and have a look around then it will say there for certain what your hard drive size is. By the way, be careful not to save any changes to the bios, or you could do some serious damage to your system. 
However, as I said, it is very unlikely that fdisk got it wrong, so you probably do just have a 40Gb hard drive.

And about the network, when you have the hardware so you no longer have to access the net via another computer then it should work with no problems at all. So as you are getting that hardware soon you might as well just wait till then.

---

### Post by Uturn-Zone on 2007-01-17
I will try something I better not say on this forum

(has to do with the W thing)
and I am 90% sure I had 80GB

so.. :S

maybe a harddrive got disconnected on my work inside... I will keep you posted

---

### Post by Extreme Coder on 2007-01-17
Why not open up the PC case and see for yourself what size it really is?

---

### Post by dbd on 2007-01-17
> **Uturn-Zone said:**
> I will try something I better not say on this forum

(has to do with the W thing)
and I am 90% sure I had 80GB

so.. :S

maybe a harddrive got disconnected on my work inside... I will keep you posted

lol, there is nothing wrong with saying the Windows word here, just as long as you say it quietly :)


If you accidently disconnected a hard drive, then that would explain it.

---

### Post by Uturn-Zone on 2007-01-18
> **Extreme Coder said:**
> Why not open up the PC case and see for yourself what size it really is?

well also a reply to dbd.
some time ago my cooler got fried in a lighting strike and I had it fixed in a computer shop. so maybe they forgot something while doing that...

anywayz.. I already had though about opening my computer.. but that will have to wait untill monday..
since I got lots of homework and I won't be home this weekend.. 
but with some luck I might get it open by tonight (don't count on it :P )

okay I will say it quietly: 
WINDOWS!!!!!!!!

quiet enough?

---

### Post by Uturn-Zone on 2007-01-27
ok I found the problem and it's fixed.. since someone thought it was funny to take the 80gb out and put a 40gb in.. 

really smart.. not!

anywayz.. got a 160 gb external hard drive now...

thanks for the help anywayz... and I bought a switch today and will get my thomson speedtouch 510 modem on thuesday.. 

if I run in some more problems I will surely contact the forums :P

---

