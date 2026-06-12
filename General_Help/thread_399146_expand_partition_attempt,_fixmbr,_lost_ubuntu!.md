---
title: "expand partition attempt, fixmbr, lost ubuntu!"
date: 2007-04-01
forum: General Help
---

### Post by cohoking on 2007-04-01
I've been rooting around these fine forums and haven't found a solution. So here goes my first post:

I've got a dual boot XP (home) and Ubuntu 6.06 system that was working beautifully until I decided I needed more space on the linux partition. The partitions were as follows:

1)boot ~2gb
2)windows ~ 50gb

3)extended (0gb)
     ext3 (linux) ~ 10gb
     data~ 30 gb
     swap~ 2gb

I tried chopping some space from 'data' and expanding the linux part. using partition magic under windows. After getting error 508 and searching the help files I, on their suggestion, downloaded and ran a some .exe's . The commands (from C:\) were:

MBRutil /RS=head0.dat
wipetrk

There was a note on how to restore what was undone (MBRutil /RH=head0.dat), but no explanation what I was doing.... The result was 1) still couldn't re partition the way I wanted and 2) received GRUB error 2 on reboot. 

I fixed the latter by booting to the windows cd, selecting the repair option, and running fixmbr (thanks forums!). Now the machine boots perfectly to windows but gives no option for linux  at all. I can't access my linux partition in any useful way and can't figure out what to do. BTW I can boot from livecd, run Gparted etc., but can't access the hard drive through the terminal... 

I was able to get some space from 'data' but couldn't add it to linux partition. The current config. is:


3)extended (0gb)
     ext3 (linux) ~ 10gb
     ext3~3gb (empty)
     data~ 27 gb
     swap~ 2gb


I would love to get Ubuntu back without wiping the partition and reinstalling... I'm guessing this gets down and dirty and after the last near fiasco I need a second opinion.

Any ideas??

---

### Post by zvacet on 2007-04-02
[http://ubuntuforums.org/showthread.php?t=398876]("http://ubuntuforums.org/showthread.php?t=398876")

---

### Post by cohoking on 2007-04-02
Thanks, 
I remember seeing this type of advice (recover a broken system) but don't recall seeing that option when booting from LiveCD. I'll give it a go when I get home from work.

---

