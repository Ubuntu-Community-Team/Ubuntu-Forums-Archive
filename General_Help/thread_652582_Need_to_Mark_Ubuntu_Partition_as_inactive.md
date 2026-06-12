---
title: "Need to Mark Ubuntu Partition as inactive"
date: 2007-12-28
forum: General Help
---

### Post by Trey_Alvari on 2007-12-28
After using partition magic to resize a vista partition Vista suddenly lost ability to boot. Each time is give me blue screen error 0x0000007b, the solution to which i have tried and it has failed. I have tried to do the start up repair which I get an error that there is an external media that needs to be disconnected, which of course there is none. After some effort i have come to believe that it is because the sda1 partition where vista is is marked as inactive. Well from the WinXP and a command prompt in windows vista I have tried to mark it as active. All attempts have failed. I think that if i just mark the ubuntu Partition as inactive then i will be able to mark it as inactive. Oh yeah I should also mention that Ubuntu Gusty cannot mount that partiticular partition because of this error:

Mounting /media/sda1/ failed. 

Hibernated non-system partition, refused to mount. 
Failed to mount '/dev/sda1': Operation not permitted 
The NTFS partition is hibernated. Please resume and shutdown Windows 
properly, so mounting could be done safely.

To those of you who say "just restart windows" tried that before vista failed and nothing.

I geuss i have two problems but i would like to get vista fixed first so please if possible tell me out to render the ubuntu partitions and GRUB inactive. I can bring them back if all else fails. I do have access to a third OS of winXP. Anyway thanks in advanced.

---

### Post by Craigus on 2007-12-28
If you use the gparted live cd you should be able to do what you wish:

[http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")

---

### Post by Trey_Alvari on 2007-12-28
alright ill give it a try

---

