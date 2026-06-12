---
title: "Shut down improperly now wont restart"
date: 2007-11-14
forum: General Help
---

### Post by USFMD82 on 2007-11-14
I have been having power problems and my battery on the laptop was dying, so I went to shut down UBUNTU and it was in the screen getting ready to shut down when he power cut off. Bow when I choose Ubuntu (I have 2 separate partitions XP/UBUNTU and if I don't click anything it auto chooses XP) when I go to reload Ubuntu it goes to the black screen and shos a few lines of code or something like that and then pops up with a screen giving me 5 options (sort of like windows screen to choose safe mode)

The options are (not exact, hopefully youll know what I am stalking about) if needed I can write down what the screen says)

UBUNTu 2.10.6
UBUNTU 2.10.6 (Recovery Mode)
UBUNTU 2.10.6
UBUNTU 2.1.06
Ubuntu megmetx*
Ubuntu Generic

Then under that it gives me the option to "C" for command line "E"to edit and something else, let me know if there is something I can do to fix it, I hope I havent royally screwed it up, I read someone  went into he BIOS and fixed the power settings or something like that, I dont know if that would do it because their problem was different from  mine but not entirely, also I dont know how to do it.

Thanks in advance for your assistance

---

### Post by USFMD82 on 2007-11-14
Is this in the wrong sub forum, or do I need more information?

---

### Post by Necromantis on 2007-11-14
Try UBUNTU 7?.10

I always get that menu with a dual boot option.. If you hard stop Linux you should get some 'insult' when you restart but it should restart. It will take a bit longer since it has to check for data which are now corrupted...

---

### Post by Goombie on 2007-11-14
What (I think) you're seeing there is the GRUB boot menu. Essentially, it's a small program that lets you choose which operating system you want to start when you turn your computer on. So, choose the regular Ubuntu option (usually at the top of the list), and see what happens. :)

---

### Post by atlfalcons866 on 2007-11-14
boot the live cd
go to terminal and type in
sudo fsck
make sure your hard disk partitions are unmounted first as fsck can cause severe corruption on a mounted partition

---

### Post by USFMD82 on 2007-11-14
Thanks for the replies, I don't have a live CD, how do I get one. I forgot to mention as well, when I click all of them nothing happens unless I hit the last one (the generic one) then it looks as if it wil boot up, and runs some lines, then shows me the startup (Ubuntu logo with the orange progress bar.. then the screen goes blank once the bar gets all the way, then it automatically begins shutting down again. So, still not sure what I  do here, thanks for your patience in helping me

---

