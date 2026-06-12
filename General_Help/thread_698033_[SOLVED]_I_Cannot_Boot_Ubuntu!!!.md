---
title: "[SOLVED] I Cannot Boot Ubuntu!!!"
date: 2008-02-15
forum: General Help
---

### Post by mwx10 on 2008-02-15
Hi,

Somone please help me. I booted ubuntu this morning and I love it.  But now i cant get past the loading screen. It only gets to 3.5 bars.  PLZ help me. I have little expirence with liunx so I need step by step instruction.



Thanks so much,
Matt

---

### Post by mwx10 on 2008-02-15
sorry i know this is rude but i really need help

bump

---

### Post by mwx10 on 2008-02-15
bump

---

### Post by accatagon on 2008-02-15
Ok. . . I'm going to need to ask some questions:
is this a brand new installation of Ubuntu?
Have you booted successfully from the hard disk before?
Is there any critical data on the partition or disk onto which you installed Ubuntu?

---

### Post by mwx10 on 2008-02-15
yes i installed yesterday
yes i have booted sucessfully
YES the data is CRITICAL!

(if a format is what you are about to suggest i cant do that)

---

### Post by accatagon on 2008-02-15
I also need to know if there are any other operating systems installed, and preferably a little more information about your setup.

---

### Post by mwx10 on 2008-02-15
yes Windows XP media center edition

it is the 4GB instalation of standard ubuntu using wubi

---

### Post by accatagon on 2008-02-15
OK. . . no format. . . I'm going to guess you didn't do anything recently to blow it up or you would have told me. 

Your data is most likely recoverable even if your system is not salvageable.

---

### Post by mwx10 on 2008-02-15
ok, thanks. The data on windows is EXTRAMLY importent the data on ubuntu i could care less about. But they are installed onto the same hard drive

---

### Post by accatagon on 2008-02-15
Did you only have 4 gigs? Gnome will not start up properly if you have almost no hard disk space, so if you ran out, that could be a problem. That's one possibility. You can try booting into recovery mode. If that works, then we will know it's not a kernel issue, and that will narrow things down a lot.

---

### Post by mwx10 on 2008-02-15
I have to go now. I will try to reply ASAP. But that might not be possible tonight.

---

### Post by mwx10 on 2008-02-15
i dont know how to reboot into recovery mode. I have pleanty of hard disk space but my dad would be PISSED if i installed the 15GB version.

---

### Post by accatagon on 2008-02-15
By the way, you need to use "shutdown -hP now" to turn off if you log into single user mode (recovery mode)

---

### Post by mwx10 on 2008-02-15
to be exact i have 154GB of free memory

---

### Post by accatagon on 2008-02-15
It should be the second option in grub. It's actually called recovery mode in ubuntu. All you need to do is type in your user name and password if it gives you the prompt, then turn it off with "shutdown -hP now." If it gives you an error, tell me what it is.

---

### Post by mwx10 on 2008-02-15
i cant even get to the prompt. hehe. *im screwed arnt i*

---

### Post by accatagon on 2008-02-15
You don't need 15 gigs, but 4 gigs is shaving it really close. . . I use 6 or 7 on one of my computers.

---

### Post by accatagon on 2008-02-15
What error message does it give you? Or are you simply confused about how to get there. Can you boot windows at all?

---

### Post by mwx10 on 2008-02-15
so ur suggesting i wipe it then do a reinstilation

---

### Post by mwx10 on 2008-02-15
im running windows fine. (now infact) I just cant even load ubuntu i gets to the orange loading bars then randomly freezes.

---

### Post by accatagon on 2008-02-15
I'm not suggesting anything yet. . . I need more information. I'm concerned about your data first and foremost. Is it safe and accessible. If it is, then that is one good thing. After that, I am concerned about the ubuntu install. When I ran out of hard disk space (admittedly in Debian and not Ubuntu) all I had to do was delete this huge file that was causing the problem. It is entirely possible that it is not the problem. A good way to check would be to load the live-cd and check how much disk space you have by going to system->accessories->disk usage analyzer.

---

### Post by mwx10 on 2008-02-15
oh come to think of it i was installing somthing before the problem started... =\

Is there anyway i can allocate more memory without wiping the installation.

---

### Post by accatagon on 2008-02-15
If it is completely full I would try expanding the partition with ubuntu on it and seeing if that lets you boot. Otherwise, you can reinstall if you really don't care about the data. If you have to move any partitions in order to expand the Ubuntu one, you should back up your data first.

---

### Post by accatagon on 2008-02-15
Sorry, I should explain how to do that. . . Load the liveCD, then go into the terminal and type "sudo fdisk -l" and copy and paste the data here.

---

### Post by mwx10 on 2008-02-15
by partition do you mean a hard disk? or some sort of virtual drive?

I install ed using wubi on my only hard drive (c:/) I did this in windows wich you probibly know a lot about but if you have never used windows (which i doubt) then it might be hard for you to help me

---

### Post by accatagon on 2008-02-15
The terminal is found under applications-> accessories

---

### Post by mwx10 on 2008-02-15
i know that. I am running windows now. NOT ubuntu. This is my only other OS I have no other liunix OS except ubuntu. Which is not working

---

### Post by accatagon on 2008-02-15
No, I know a lot about windows. . . Sorry . . . I just assumed you had installed from the liveCD (I know I know. . . I just forgot). Generally I do partition resizing off of a live-cd (a special CD that boots linux without any installation). . . I need to see if I can find a program to do it under windows. . . Windows can only resize it's own partitions, not ext3, which is what ubuntu uses by default.

---

### Post by mwx10 on 2008-02-15
hehe I didnt mean to sound sharp I was just presenting some facts. Hmmmmm im in quite a delemia arnt I

---

### Post by mwx10 on 2008-02-15
let me try booting ubuntu again.

---

### Post by mwx10 on 2008-02-15
I have no idea what the hell(pardon!) just happened. Ubuntu booted fine. I am speeking to you now on ubuntu. (not in recovery mode)

---

### Post by oilchangeguy on 2008-02-15
> **mwx10 said:**
> ok, thanks. The data on windows is EXTRAMLY importent the data on ubuntu i could care less about. But they are installed onto the same hard drive

you have no issue with your data, since it's safe in your windows install. and you are (were) running ubuntu via wubi. just go to the windows control panel, add/remove. and uninstall wubi. and say bye-bye to ubuntu. then run a dual boot setup the correct way. from wubi's website it's beta software. and when beta software breaks something, you get to keep both pieces. never depend on beta software.

---

### Post by accatagon on 2008-02-15
OK. . . I can't find any program that will run in windows. . . If you want to resize your partitions, I would recommend a live-CD. There is one at [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/). This CD is only around 50 megs and will let you graphically resize your partitions. The problem with this is that You need to know which partition Linux is installed on. If you would feel more comfortable with full fledged Ubuntu on a CD, you can get the Ubuntu Live-CD here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download), but it's a full 700 megs. 

Do you know which partition is your linux partition and do you know how to boot from a CD?

---

### Post by mwx10 on 2008-02-15
well its working now. (oddest damn thing....)

---

### Post by mwx10 on 2008-02-15
i think so. Its in a folder in /wubi/drives/ Yes i can boot from a CD. but is it the full ubuntu and will it replace my current ubuntu and windows instillation if i run it

---

### Post by mwx10 on 2008-02-15
Well its working fine now so i think we can feal safe to call this resolved.  I do want to take measures to find out what caused it.

---

### Post by mwx10 on 2008-02-15
i know you have many posts and you are expirenced. but wubi is clearly not the problem(blatent facts here not me being a liunix n00b =) )
I have run it before and i am now. It was probly just a problem with my system (computer not ubuntu or windows) 

Thank you all for your time especially accatagon  who willingly donated his time to me and my rather petty problems :-) thank you once again and I hope to be privilaged to work with you again. I will look into the whole live CD thing.

Bye,
mwx10

(thanks again)

---

