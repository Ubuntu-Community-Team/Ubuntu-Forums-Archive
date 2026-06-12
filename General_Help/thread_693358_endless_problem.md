---
title: "endless problem"
date: 2008-02-10
forum: General Help
---

### Post by pavel989 on 2008-02-10
ok so i was using a live cd as i remember to repartion my hd. ubuntu games didnt like my radeon 2600 so i didnt seen any point in keeping my ubuntu at 150 gigs since my xp could play most of the same games and maybe a few more. i think an error did occur, dont remeber.
and now the fun begins.

XP will not load normally. ive checked it countless times, reinstalled sp2 countless times.
itll boot after a reinstall which takes much more then the time left of that damn blue screen from hell.

so itll load, and then when i try to update, it wont. then when i reset, it wont boot. well, it does boot but into like XP 2000 theme and mostly everything wont work. Dell wont help and ive tried many many things from ubuntu to try and fix it.

also as usual the installer cant find files that are blatently on the cd. i dont really wanna completly reinstall since it cant find files (also i ran that command in xp to check if my install is full) and itll take a while.

so i turn to the only place i know that has some help and sense, the ubuntu forums.

if anyone can help, i really wanna tackle this.


some erros ive been getting all around were that $LogFile is messed up, and windows journal file is unclean.

---

### Post by src2206 on 2008-02-10
Correct me if I am wrong- you did not install Ubuntu on your HDD, right? If you have been using Ubuntu Live CD through out without installing anything on your HDD, then the problem with your windows should have nothing to do with Ubuntu.

Did you run a complete Virus Check of your Windows installation? BSOD can occur for various reasons, so you need to eliminate on e by one to reach the real cause. Why did you think that it is Ubuntu Live CD to blame?

Please furnish these info, I shall surely try to help.
:)

---

### Post by Fernanernie on 2008-02-10
Can you boot with the M$ CD to the Recovery Console and type in' bootcfg /rebuild' and/or 'fixmbr'? 
Without the quotes of course

---

### Post by pavel989 on 2008-02-11
ill try that asap Fernanernie.

src2206- i am not blaming ubuntu at all. if not for visual studio, id probably switch over to ubuntu completly, my other old computer is only ubuntu. i prefer ubuntu of xp, but XP has a lot fo things that ubuntu cannot so i still use it.

with that out of the way: no i have ubuntu on my hd, but i was using a live cd to repartion.

BTW i wanted to mention, i waited longer in a que for dell help and got nothing out of it except for help to wipe my hd and reisntall xp. mind them i did say xp couldnt install normally, and if managed to use linux, idont think id need help isntalling xp.

---

### Post by pavel989 on 2008-02-11
ran the commands, now my pc won't boot into ubuntu or xp. yet again, xp has ruined my day and stole hours of my life I won't get back.

Its running chkdsk right now in the recovery. I'm on my fone right now. but yea I think just wipe, and reinstalling my dualboot is now the only way to go. but that's a last resort, and there has to be a way to fix this!

---

### Post by src2206 on 2008-02-11
It appears that your MBR is messed up and chkdsk is not going to solve the situation for you, 'cause this command fixes any error if available in the disc.

I suggest that you run fixmbr again from recovery console. If that still does not solve your problem, do a "**repair install**" of XP. If you do not know how to do a repaire install, please post here, I shall try to help you out. :)

BTW, I believe that there is a slight misunderstanding; I never meant to say that you are blaming Ubuntu. I was thinking whether you have any reason to believe that some problems in Ubuntu might have caused the problem. ;)

If you can repair your XP, you can always use XP boot loader to boot in Ubuntu provided your Ubuntu installation is still intact, or you can reinstall the GRUB of Ubuntu in a Floppy Drive or USB stick without disturbing the XP MBR.

---

### Post by pavel989 on 2008-02-11
(huge amounts of loud cursing and devilworshiping)

well first off, turns out my computer was never broken, and i did fix my computer the first time i tried on my live cd. i ran the commands, ima fix grub later. 

heres the break down

i was using a program called magiciso to mount iso files as a cd so that i could play a prated cracked game. oddly enof the no cd crack didnt work. i just had a thought that it could be causing problems, and saw that when i load into that weird version of xp, drivers are all weird. so i uninstalled it, deleted my catroot2 folder so that i can update. while i cant update, i can get into my xp, me thinks. 

so yea. if u know of a better program to mount stuff, id like to hear, but apperently thats where my problem was.

LINUX TO THE RESCUE!!!!

---

### Post by Jay Jay on 2008-02-11
> so yea. if u know of a better program to mount stuff, id like to hear, but apperently thats where my problem was.


Have you tried [Daemon Tools?]("http://www.daemon-tools.cc/dtcc/download.php?mode=ViewCategory&catid=5") If not, then that's what I recommend. A word of caution about using pirated/cracked Windows games: becareful. You leave yourself wide open to all kinds of grief such as the risk of hidden Trojans, Viruses and other equally unpleasant malware. I ended up losing my MBR and suffering a hard disk corruption, even despite scanning the game files prior to installation.

---

### Post by pavel989 on 2008-02-11
well i got a really good antivirus, but that doesnt mean i wont get a virus, i know. quite frankly i think i do. idk maybe not but i have logmein installed, and it says my computer at home is off, and iwas using it today. so yea maybe i didnt fix it. are there like any unkown ubuntu apps to help fix ntfs\xp

---

