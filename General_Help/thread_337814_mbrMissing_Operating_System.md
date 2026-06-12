---
title: "mbr/Missing Operating System"
date: 2007-01-13
forum: General Help
---

### Post by paulyj1124 on 2007-01-13
Hey everyone,
Was wondering if you guys could help me.

I was rearranging the partitions on my other computer, and I decided to remove the Linux partition and give the whole hard drive back to Windows again (of course I was gonna install linux again later). 

After using partition magic to delete the linux partition and merge the freespace with the windows partition and rebooting I got a grub error and I decided to fix the windows mbr. I dont have a floppy drive on my other comp or the windows recovry cd, so I made a windows 98 cd (and a DOS 6.2 cd just in case,) and booted that up and did the command: "fdisk /mbr" After I did this and restarted I got the error Missing Operating System. So I booted up knoppix and I saw my windows hardrive on the knoppix desktop so I clicked it and was able to browse through. So I guess my windows partition is still there but its not booting up? Can anyone help?



-thanks

---

### Post by wireddad on 2007-01-13
Can you get to the recovery console?  Which version of windows?

---

### Post by paulyj1124 on 2007-01-13
I'm using Windows xp home edition no service packs

the recovry console is from the windows install cd right? I dont have the cd though.

---

### Post by wireddad on 2007-01-13
If I am not mistaken, you can get to the recovery console without the CD.  I will have to do some searching through save data.

---

### Post by wireddad on 2007-01-13
You are right.  You will need the CD for recovery console.  Still reaching though.

Researching that is...not reaching.

---

### Post by wireddad on 2007-01-13
Try this:

[http://www.ubuntuforums.org/archive/index.php/t-311908.html](http://www.ubuntuforums.org/archive/index.php/t-311908.html)

---

### Post by paulyj1124 on 2007-01-13
I did a mbr fix from the super grub boot disk now there a knew problem everytime I start up the comp I get "Error loading operating System" instead of missing operating system....hmmm

---

### Post by wireddad on 2007-01-14
I am not sure.  Usually when silly thing like this happens to me I just reload completely after trying and trying and nothing seems to work.  Is it possible to transfer your important data using Knoppix ten reload?  Probably no since you did say that you do not have the OS CD, right?

One other:  [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

I believe it says you can edit the boot loader.
"
 GRUB[[5]]("http://www.gnu.org/software/grub/") / LILO[[6]]("http://home.san.rr.com/johninsd/pub/linux/lilo/lilo-22.7.3.lsm") are the most common bootloaders used with Linux. You can restore your bootloader from this SystemRescueCd. For example, if Windows removed Grub, you can run grub from this CD, and reinstall this bootloader."I have not used this yet so not sure how to do it.

---

