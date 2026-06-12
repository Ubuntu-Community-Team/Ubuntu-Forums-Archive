---
title: "Gone /home partition?"
date: 2007-04-17
forum: General Help
---

### Post by zeekay on 2007-04-17
Greetings!
 
I used to have stable installations of both Ubuntu Dapper and Windows XP, booting though GRUB and so on. Everything was going preety well until yesterday, when I tried to remove Windows XP partition, in order to resize it to a smaller size, and install Windows Vista, for testing pruposes. So on, I entered on my Ubuntu 6.06 Live CD, re-made the NTFS partition, and installed Vista.
 
Of course, it wrote on the boot sector of the HD, so I couldn't start Ubuntu again. So, I booted the live CD again, tried to mount my Ubuntu "/" and "/home" partitions and backup the useful files on DVDs, and re-install ubuntu again. For my surprise, when I ran the liveCD install to get on the partition manager, and find out their names (sda3 and sda4), it claimed that the "sda3" was on the ext3 file system, and the "sda4" (which is the /home) on no filesystem at all! I tried to mount the sda3 (the "/") and it mounted the the liveCD files instead. Tried to mount the "/home" or sda4 partition and nothing happened!
 
Okay, this time I thought this wasn't easy. SO, I went to google and run some grub commands I've found on this forum though the liveCD, with the hope that at least I could boot my HD through it. I went to the terminal and put:
 
```
# grub
> find /boot/grub/start1
(sd0,2)
> root (sd0,2)
> setup (sd0)
> quit
```
 
And I rebooted the pc. GRUB showed up, exacly the same way it would do before the whole mess, with the Ubuntu, memtest and windows XP options, just the way it was, BUT, I could only boot on windows. The other options only returned me a big and sad: **ERROR 15: File not found.**
 
Is my data lost for ever?! I really need some help on this, at least so I can be able to backup some files I need most and then install Ubuntu from scratch again.
 
Thanks in advance and excuses for the bad English.

---

### Post by dfreer on 2007-04-17
When you delete partitions and create new ones it tends to shift your partition names around, this may be what happened to you...

---

### Post by zeekay on 2007-04-17
You mean, the "/" partition that was before called sda3 is now sda2? I tried to mount all the partitions I had before and now, and I only successfully mounted a "/" but didn't had my data in it, such as my edited xorg.conf and it's backups. Comparing to the liveCD system, it was the same, which made me believe I only "re"-mounted the liveCD onto another directory... :( 

I'll try a few more commands as soon as I get home, but any suggestions on where and what to try would be welcome.

Thanks :)

---

### Post by dfreer on 2007-04-17
If nothing else, you should be able to grab all of your data off the hard drive from the live CD and install from scratch. but you shouldn't have to do that it sounds like grub is just pointing to the linux partitions wrong, maybe because the names changed.
try mounting your /boot (or / if you didn't create a /boot partition) from the livecd. from there post your /boot/grub/menu.lst

---

### Post by zeekay on 2007-04-18
> **dfreer said:**
> ... but you shouldn't have to do that it sounds like grub is just pointing to the linux partitions wrong, maybe because the names changed.
try mounting your /boot (or / if you didn't create a /boot partition) from the livecd. from there post your /boot/grub/menu.lst

Finally yesterday I was able to mount my partitions from the liveCD. The key for it was trying to mount them on /media and not on /mnt, like I was doing before. So, I was able to backup my files to another PC on my network. :) Nothing to worry, it's my wish to re-install it from scratch and I will do it as soon as I download Feisty. Another question now: should I create a separate partition only for "/boot"? If you guys think it is useful, I might try. :)

Thanks for the help so far.

---

### Post by dfreer on 2007-04-18
It used to be that it was wise to create a /boot partition (only needs to be 100 mb's at most) when dual booting with windows. Can't remember quite why, but it had something to do with the BIOS being unable to boot partitions past a certain point, like maybe the first 1024 cylindars? Don't quote me on that lol, but you would create a /boot at the beginning of the HD, creat a windows partition that started within the 1024 limit, and then partition the rest of the HD as you see fit. Since both windows and /boot were within the 1024 limit, BIOS could boot either OS. 

This no longer is needed on newer PC's, the only other reason I could think of for having a seperate /boot is if you are dual-booting two linux OS's. You could then share the /boot partition (along with /home) between the two. No need for it really, but having the seperate /home partition is a GREAT idea :D If you run into this problem again, you could safely reinstall without losing your files!

EDIT: this might help you understand the 1024 limit if you really wanted to know: [http://wiki.debianhelp.org/pmwiki.php/DebianAnatomy/BootDir](http://wiki.debianhelp.org/pmwiki.php/DebianAnatomy/BootDir)

---

### Post by zeekay on 2007-04-19
Heh, thanks for the tip, I'll try that. About the separate /home, I'm using it since I got Dapper installed on my pc, and it is indeed useful. :)

Today, after the network backup, I re-made my linux partitions and installed Feisty. Everything seems to work ok now. Thanks for the patience. :D By retribution I'll stick around this forums and help more users with my knowledge about this OS we love so much.

---

