---
title: "Need help removing Ubuntu."
date: 2008-04-03
forum: General Help
---

### Post by jamesatqmul on 2008-04-03
Hey,

Here's it simple, I tried Linux for the first time about 2 months ago (Ubuntu..obviously) and frankly, it's not for me. It's too technical, I can't play my games, I can't use my favorite programs, and its playing up on my home network..... Result: my desktop is constantly off and I'm using my laptop instead.

I want to re-install Vista on it. However, It won't let me format the disks. What I need, is instructions how to get my disk partitions back to NTFS. I'm not sure if this is because of some weird filesystem linux uses, or my copy of vista is buggered. I can't stand XP so thats no option.

I don't want a 'why don't you try and dual boot..bla bla bla' I've tried linux and I don't like it :) I want it off my PC! Sorry lads, Ubuntu is nice but it's not useful for someone like me.

I have technical experience, but I don't want to have to faff around in the command line, is there a program which will let me just wipe the disks then boot off my win CD?

Cheers

---

### Post by sekinto on 2008-04-03
Vista should be able to format the drive no matter what its state is.
I guess if it really can't you can do this:
> 
1) Boot up your Ubuntu Live CD
2) Open gParted
3) Select each partition and delete it
4) Hit apply

Then Vista should be able to "see" your drive.

Or you could take one of the easier routes of wiping your hard drive (taken from the malicious commands announcement):
> sudo mkfs YOURDRIVE
But you will still have to boot from a Live CD to do that.

---

### Post by jamesatqmul on 2008-04-03
thanks, I will try the gparted now..

---

### Post by ugm6hr on 2008-04-03
Any of the Hard Disk Wiping tools linked from here: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) will erase everything for you.

---

### Post by matey3 on 2008-04-03
> **ugm6hr said:**
> Any of the Hard Disk Wiping tools linked from here: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) will erase everything for you.

Thanks for the link.
 lol tho bcs I have a desktop with Vista and I want to put Ubuntu on it because the vista I have is sooo annoying! None of my old programs/drivers work on it even my Norton anti virus does Not work on Vista?!
the search for files sux big time and basically I love to have my XP back.but i like ubuntu much better.
may be it is the super professional version of it that is no good? may be there are vista which work good? I dont know?

but to be fair, all operating systems i have tried have problems with memory and require you reboot them after being on for a long time? even my ubuntu feisty gets really slow to the point that I have to use reboot command otherwise no go..??

---

