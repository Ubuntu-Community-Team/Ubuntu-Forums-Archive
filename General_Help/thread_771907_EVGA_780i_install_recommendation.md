---
title: "EVGA 780i install recommendation"
date: 2008-04-28
forum: General Help
---

### Post by justgimmeascreen on 2008-04-28
Hey guys,

I just built a computer using an E8400 in a 780i motherboard and a 8800gt graphics card, and I was wondering if anyone could recommend a particular version of ubuntu over another.  I have been using Gutsy on my laptop for well over a year now, but I don't know how well Hardy has been received by the community.

Any warnings or advice is appreciated....

---

### Post by GrokIt on 2008-06-06
If you want to install Ubuntu 8.04 you will want to use the alternate CD (text version) because the EVGA 780i mobo does not have a VGA connection.  If you want to install Kubuntu 8.04, use the safe graphics mode.  I had a lot of problems trying to use the regular install for either one.  Both will work.  The only thing is to ask yourself is what do you want on your rig?
When you first start up you will get a display error and your screen will be in something like 600 x 480.  Don't worry.  Get envy from the repros and you will be up and running in minutes in hi res.  I ran envy from the cli and it worked very well.  Got all my eye candy up and running.
When I built mine the E8400 was sold out, I'm jealous :)

---

### Post by justgimmeascreen on 2008-06-12
Thanks for the info,

My goal is a dual boot system that runs XP for games and Ubuntu for everything else.  So far I have been using Ubuntu on my laptop and I wanted to started using it on my desktop more.  I haven't been able to keep up to date on how well the new versions of Ubuntu have been working, and I just thought I should ask before I start installing.

Thank you for the help!

---

### Post by GrokIt on 2008-06-16
Sounds like you're doing what I did.  The way I got a dual boot going was to hook up my slave disk to the first sata port and install XP on that.  Then I moved it to the second sata port and only then plugged my master disk into sata 1, rebooted and installed Ubuntu on that.  Grub picks up the second OS with no problem.  I also made a directory off my $HOME folder and used that to auto-mount the XP disk.  The only drawback to this method is that my Kubuntu can read/write to the XP disk but Windows has no idea the other disk exists.  I'm happy with that but it may not be for you.  
I've just started playing around with VirtualBox to see how Oblivion runs.  I haven't been able to complete the game install yet.  It starts but craps out half way through.  It is pretty cool seeing windows running inside linux though.

---

### Post by omegamike3 on 2008-06-16
I have the same board and installed off the standard 64bit Ubuntu Live disk without any problems at all. I did partition my main drive between XP for gaming and Ubuntu for the rest. If you want to read your ext partition from windoze, [this]("http://fs-driver.org") works quite well, IMHO. :)

---

### Post by GrokIt on 2008-06-20
I might check that out someday omegamike3.
I had a big problem with my box last week, it stopped booting as soon as it turned on.  Nothing. At. All.  Very upsetting after spending all that $$.  Apparently the 780i boards may just crap out at anytime with an FF error.  Google "instant FF" and you will see what I mean and all the round-about fixes.  Long story short, here's what actually works: remove the battery from the mobo for at least 15 minutes.  That was the last thing I tried, you want to try it first if it happens to you.
Update running Oblivion in Virtualbox: don't even try it.  Seems that vbox makes up it's own virtual hardware and it doesn't include anything 3D.  You can install it perfectly but just can't play it :roll:      I then tried Cedega (a Wine fork for gaming) and technically got it running using Oldblivion.  The frame rate goes from really good to really bad.  I may have to play with the settings some more.  There are problems with the pixel shading 2.0 using the regular Oblivion but this may be fixed when Cedega 7.0 comes out soon. <sigh> Still need XP for something <sigh>.

---

