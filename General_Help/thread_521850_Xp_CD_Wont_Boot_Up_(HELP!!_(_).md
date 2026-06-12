---
title: "Xp CD Wont Boot Up (HELP!! :( )"
date: 2007-08-09
forum: General Help
---

### Post by xImEtH on 2007-08-09
Ok guys so here's the deal: (excuse my english, im from Puerto Rico and a LINUX NOOB)

I have both Windows XP Proffesional and Ubuntu 7.04 (feisty Fawn) 64-Bit Edition going on dual boot. I was having both OS in a 200GB HD, running flawlessly, i installed xp first then ubuntu. 40 GB for XP, 135 GB (NTFS) for storage (videos,music,pictures,etc.), and 10 gb for ext3 (Linux), a 1gb swap partition, and a 4 gb partition for my /home folder so i dont lose my linux documents....ok...so...it turned bad...a day ago:

I was messing around with XP and I installed Cursor XP (a prog to modify mouse cursors) and had to reboot to finish installation so the mouse cursors would display properly. I rebooted, then when the XP logo appeared it just kept loading and loading but eventually the progress bar stopped and the system completely froze...my HD light was lit on all the time... so i rebooted once again but the problem happened once again...so i decided to go into safe mode. Everything in safe mode ran smoothly and i uninstalled every bit of information and registry that was used by cursor xp, i used ccleaner. Then i rebooted once again to load full windows xp....but the same problem appeared...so i decided to repair my installation in case it was some of the boot files from XP....Guess What...XP CD wont BOOT!!!..... all it said was "press any key to boot from cd" ..so i press a key and and the screen goes blank like forever.......so ive got 2 problems basically...i Cant boot from my XP CD..(tried changing boot orders, 3 different XP cds, my dvdrom drives are in perfect condition) and my XP logo freezing problem.......i dont care much about my XP logo problem since that has an easy solution.....what i Cant seem to find is the solution to why my xp cd wont boot....i really want to keep both my XP and Ubuntu partitions since both are running perfectly......is there anything i can do in safe mode or any code i can input in the terminal in linux so i can finally reach my xp cd menu in order to restore my xp and be once again a happy person??:(....

---

### Post by kast on 2007-08-10
Did you try the Last Known Good Configuration before booting into safe mode and messing with the reg?

---

### Post by xImEtH on 2007-08-10
i did it already and it gives the same result.......start windows normally and last known good confugration wont work...only safe mode... but i dunno what to do in safe mode to restore my xp.... y already uninstalled and cleeaned the registry for the cursorxp program i installed....but still...windows xp logo splash screen hangs forever

---

### Post by kast on 2007-08-10
Do you have a floppy drive? you could  download the xp boot ([http://www.microsoft.com/downloads/details.aspx?F](http://www.microsoft.com/downloads/details.aspx?F) amilyID=e8fe6868-6e4f-471c-b455-bd5afee126d8&DisplayLang=en) floppies i think its six in total this will allow you to go to repair console the commands are fixmbr then fixboot
then exit reboot the pc


not sure if fixing the MBR with mess with the linux load, but it would be easy to manually edit the xp boot to include the second partition/hard drive.

you might also be able to boot to safe mode with command prompt and then access the cd from there.

---

### Post by xImEtH on 2007-08-12
but itsnt that the same as loading the xp cd in....i mean..would it make the mbr work??
do they work the same?? the xp cd or the xp boot disk

---

### Post by kast on 2007-08-12
Can you do the same thing with the Floppy's YES but its not using the same hardware to get there. the commands  

[B]fix MBR
fix boot[/B]


can be executed from the floppy's also.

---

### Post by xImEtH on 2007-08-12
ohhh thanks...ill try it out and see how it goes..thanks kast

---

