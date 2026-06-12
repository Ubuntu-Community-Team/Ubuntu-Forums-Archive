---
title: "Can't get a boot menu for my dual boot. Locked out of BOTH OS!"
date: 2008-01-28
forum: General Help
---

### Post by stcninja on 2008-01-28
Here's the problem, I have a dual boot system on the same HD. Windows XP Pro and Gutsy Ubuntu. My windows effed up on me so I switched to Ubuntu and have been using it ever since. However, I decided to try and fix the Windows OS. As I started up from the XP CD and went to try and install it without doing the full formating thing because I didn't want to lose all my files and such, it said I couldn't because it didn't recognize the partition. So I'm like, "Oh well, I don't REALLY need it anyways" so I go restart and Lo and Behold GRUB or whatever the default Ubuntu thing is doesn't come up and I can't get into either OS because my computer just sits there.

So Im thinking that my boot thinger got messed up a little when I put the Windows CD in and booted from that.

I'm in LIVE right now

Here's a readout I get from "sudo fdisk -l" about my HD but it's totally wrong. I should have the windows partition which as I remember was NTFS. and the Ubuntu one was the default format or whatever. The windows partition is supposed to be 150ish GB and the Ubuntu around 10GB.

Disk /dev/sda: 164.6 GB, 164696555520 bytes
161 heads, 15 sectors/track, 133197 cylinders
Units = cylinders of 2415 * 512 = 1236480 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      111154   134217727+   4  FAT16 <32M

Disk /dev/sda1: 137.4 GB, 137438952960 bytes
161 heads, 15 sectors/track, 111153 cylinders
Units = cylinders of 2415 * 512 = 1236480 bytes

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   *           1      111154   134217727+   4  FAT16 <32M

I figured I just needed to get into my /boot file whatever it's called and correct whatever problem the XP CD (if that is what messed things up) caused. but with this pleasant surprise of alien partitions I have no idea what to do.

---

### Post by slayer04 on 2008-01-28
MBR which was grub must of been replaced because of your XP tinkering so just reinstall Grub and you should be set to go 

but I myself do not know where it get Grub but I am sure you can use the live cd to download and install it  maybe just Google it


p.s those 2 - 32MB partitions are both from windows because for some reason you need to leave 32 MB open for windows I know cause I had to do the same for my install of XP so you should leave those or if you decide not to use windows any more, use the live cd  and gparted to merge the 64MD into your ubuntu partition

---

### Post by stcninja on 2008-01-28
yes yes. thanks.

I can find some nice walkthroughs with commands and everything for restoring GRUB
only problem is they're not working. can't find the stage 1 file. so I try mounting my root partition like some thread points out but only problem is I don't know where my root partition is because when I do sudo fdisk -l it spits disks I don't really recognize.

---

### Post by kryth on 2008-01-29
i'm on windoze ATM, so this is from memory. If you can mount you linux drive, you can find the info you need for the Grub walkthrus in a file called menu or something like that inside boot/grub or something close. It will be near the bottom of the file and look like (hd0,5).
Sorry can't be more helpful ATM. But it may be step in right direction.

---

### Post by ronmarley1 on 2008-01-29
Another option is to try the SuperGrubDisk.  It has helped me a few times.  You can download the iso here: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)  Burn the image to a CD and boot the CD.  Follow the prompts to restore GRUB.

---

### Post by stcninja on 2008-01-29
I tried the SuperGrubDisk but to no avail.

Do you think it's possible that when I was in the XP install CD and canceled it (Due to not wanting to have to do a full format of everything =/ ) that my partitions could have just been deleted?

Thanks

---

### Post by greypoet on 2008-01-29
I await with baited breath, the outcome of your discussion. Similar problem: can't boot into XP. "ntldr missing. Press ctrl+alt+del to restart"
And supergrub didn't help me either.  :confused:
Good luck.

---

### Post by kryth on 2008-01-30
I'm out of ideas.
Reinstalling and starting from scratch ain't the end of the world. 
You may learn something, atleast that's the way I  *try* to look at things.

---

### Post by greypoet on 2008-01-30
**stcninja**, why don't you take this over to the "Absolute Beginners" forum? You don't sound like you *quite* fit but... Who knows?

---

### Post by stcninja on 2008-01-30
Yeah. Im pry goina to completely redo everything and start clean. But I just want to get all my music and pictures and whatever else I need (like Blender files! D=) off. I've redone my system a few times before and I think it's a healthy thing to do from time to time (at least with windows)

no beer and no music make stcninja go crazy. Not a good thing since ninjas flip out and kill people =X haha.

---

