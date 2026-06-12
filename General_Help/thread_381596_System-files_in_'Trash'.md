---
title: "System-files in 'Trash'?"
date: 2007-03-11
forum: General Help
---

### Post by trax84lux on 2007-03-11
Hi

to start... I'm using an updated Feisty...

So, to my problem:

I got the trash-icon on my desktop, and there I can see that it is filled. So, when clicking on it, I got files like console, apache2, sudo, screen, hal, NetworkManager, and some other (no doubt) system files in it.

A rightclick, and 'properties' gives me a location "/var/run" with the modified date of when I booted my computer for the last time (so, this morning in my case) for all these files.

When I try to open the trash by accessing ~/.Trash there is nothing at all in the Trash (not even hidden files)

Nothing in the /root/.Trash...

So, how comes I have these system-files in my Trash (where I don't even know what trash that really is o.O)

Oh yes... btw: whenever I delete a 'normal' file, it also appears in the 'desktop'-trash

---

### Post by doghi on 2007-03-12
Hi trax84lux!

OK, I don't want to add a simple 'me too', but my problem looks a lot like Yours:

The files, I get displayed in my /home/guido/.Trash are all located in the /boot directory, not /var/run, like yours!
Also, like You, the Trash is empty, when gksudo nautilus there as root!
Because I have partitioned my drive a lot (one extra partition for /boot, one for /usr, one for /home, etc.), when I umount the /boot partition, the Trash is empty!!!
Maybe anyone here can explain me, what's going on?!?!

ciao,guido.

---

### Post by trax84lux on 2007-03-13
Hey,

I'm happy that you add this 'me too'

Because I really thought that I'm the only one having this kind of prob.
In my case I only got the /home on a different partition; for the rest, everything on the main partition.

yes, would be interesting to get a solution to this 'problem'. It doesn't affect my system at all, but it's simply quite strange

Laurent

---

### Post by doghi on 2007-03-13
Hi trax84lux and all the others out there!

OK, maybe this is helpful:

The above described phenomenon hit me on both edgy and feisty (I recently upgraded, but allready got the problem before)...

---

### Post by SishGupta on 2007-03-13
It would seem that your .Trash folder is a link to those directories.

You could try "rm -rf .Trash"

The .Trash folder is recreated automatically when you delete something in nautilus.

---

### Post by doghi on 2007-03-13
Hi SishGupta!

Allready tried that, the strange thing here is that in a terminal when I 'ls' my /home/guido/.Trash it's empty!
Which is obviously why the 'rm' doesnt remove anything!
Only nautilus shows the files from the /boot directory!
And it wont let me empty the trash, because I don't own those files!
(They're not shown as links, but as files located in /boot and owned by root)...

thanks and ciao,guido.

---

### Post by trax84lux on 2007-03-15
> **SishGupta said:**
> It would seem that your .Trash folder is a link to those directories.

Indeed... Just had a look now at the /var/run dir, and there are exactly these files, I have in my desktop/panel-"trash".

As mentioned:
- whenever I delete a file, this file can also be found in the trash (the one that I access from the desktop/panel)
-whenever I delete a file, this file AND ONLY THIS file can be found in my ~/.Trash


So, there is a difference between the trash I access from the desktop/panel and the one I access by ~/.Trash

the desktop/panel trash is kinda hybrid o.O

---

### Post by Cazzj on 2007-05-26
I'm having the exact same problem. I'm running the latest Feisty Fawn (Mar-26-2007).  When I open the Trash in the GUI I see a bunch of System files/folders like "apache2, avahi-daemon, console," etc.  They have current last modified dates too.  From the terminal though, an "ls -la" for my "~/.Trash" shows nothing.  With the GUI Trash window open I did a "sudo rm -rf *", hoping nothing would implode, but alas, nothing happened at all.  Also, if I "sudo find / -name utmp", which I see in the trash, the only result I get back is, "/var/run/utmp".  Soooo....Ubuntu is confused.

Any help from you Ubuntu gurus would be greatly appreciated.

Cheers....Cazzj

---

