---
title: "help get me off hardy"
date: 2008-05-09
forum: General Help
---

### Post by i0ls on 2008-05-09
it seems i made a tragic mistake upgrading to hardy today, and after hours of waiting for the upgrade to finish in update manager i am faced with some annoyances. ie system hangs on shut-down/reboot, cannot get nvidia drivers to actually enable though they say they are, compiz issues ect.

my issue is i have everything on this drive in my home folder and its not backed up anywhere, and i updated from gutsy to hardy. is there a way to downgrade to gutsy without doing a fresh install from the live cd? and or repartitioning the drive?
please help

---

### Post by chewearn on 2008-05-09
No, afaik, there is no upgrade-undo function; it's a one way ticket.

.

---

### Post by i0ls on 2008-05-09
this is defiantly the last time i do an upgrade trusting that it will run smooth because of the last version. gutsy ran flawlessly on this machine:mad:

---

### Post by isecore on 2008-05-09
I'm taking a wild guess here, but did you use software such as Automatix? Automatix is well-known for causing breakage in upgrades, due to the fact that it's a crappy application.

---

### Post by lessgov2007 on 2008-05-09
I also had problems with my graphics card in Hardy.  Turned out that the recommended driver for my NVidia 6200 in Hardy was causing the problems.  I ended up removing that one and using the older one.  Works great now and taught me a lesson too.  I bought a cheap hard drive so I can try out the new versions first.  Gives you a chance to work out any bugs.

---

### Post by wabbster on 2008-05-09
<vent>
I empathize. :)

I had similar problems too, so I switched back to Gutsy... Downloading 'updates' for Gutsy as I'm typing this...

Patience is the key, I guess. Hardy is bound to get better.
</vent>

Clean install to Gutsy is the only way out, I guess. You'll have to re-build most of your customizations.

Good luck,
Wabb.

---

### Post by chewearn on 2008-05-09
[SIZE=2]I guess they need to teach this in school nowadays.  Except that education systems (no matter where in the world), don't actually teaches all the stuffs you need to know. :wink:


[SIZE=3][SIZE=4]*BACK-UP*[/SIZE] your install before major changes.[/SIZE]
If you are going to upgrade, clone your OS before hitting that upgrade button.

Note I use generic "OS".  This apply to every OS in the planet[/SIZE][SIZE=2] [[SIZE=1]some says, also in other planets[/SIZE]].[/SIZE]

.

---

### Post by wabbster on 2008-05-10
> **AstalaVista said:**
> [SIZE=2]
[SIZE=3][SIZE=4]*BACK-UP*[/SIZE] your install before major changes.[/SIZE]



I quite agree. Thank heavens for flash drives! :D

---

### Post by anobomski on 2008-05-10
better still always set up your home on a different partion. in this way you can always do a fresh installation without touching your docs.

---

### Post by i0ls on 2008-05-22
yeah ill call this a tough lesson learned. no i was not using that software, i am still stuck on hardy because i cant fing a drive large enough to back up my music and files. 
still no luck wating for an update to make my system shut down or restart without holding the power button =(

---

### Post by mixmaster on 2008-05-22
I'm completely paranoid.  I clone my system onto another HD and then upgrade.  If it all goes well, fine, otherwise I just swap cables and I'm back in business.

---

### Post by Christofurriebum on 2008-05-22
If it's not too late...

Are you able to log in to the machine via ssh?  You could then use scp or some other cunning trick, to rescue your treasured data?

Also.  I tend to download and burn the latest version onto CD, then try it out using the live CD.  This has saved me a lot of hassle on some work PCs that wouldn't even boot up with the CD, though they ran Gutsy fine.  I also did the upgrade from Gutsy to Hardy on one of these test machines which went well until it needed a reboot - the end.  I'm glad I was only playing around with a spare disk.

---

### Post by wkulecz on 2008-05-22
> **anobomski said:**
> better still always set up your home on a different partion. in this way you can always do a fresh installation without touching your docs.

This is fine for your docs, but in general will cause issues with all the hidden folders of setting each application creates.  Rarely are these things cleanly reusable in newer versions of the applications.

The install to a second hard drive is IMHO the best solution. Then copy what you need from the old system and use the original drive as a backup until you are ready to upgrade again and repeat the cycle.

Hard drives are so cheap now days it make little sense to try to avoid buying one and put your data and time at risk.

--wally.

---

