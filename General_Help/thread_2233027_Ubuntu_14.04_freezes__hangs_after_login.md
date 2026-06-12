---
title: "Ubuntu 14.04 freezes / hangs after login"
date: 2014-07-05
forum: General Help
---

### Post by mjpatey on 2014-07-05
Hi, all-

I'm a longtime Ubuntu user (since 6.06), and happy I haven't had to come back here for advice in a very long  time! A very good sign.

However, I just did a fresh install of  14.04 on my main laptop, and every time I boot, it freezes immediately  after login. To compound the problem, this laptop has been rendered  screenless by my (very apologetic) 9-year-old son after it succumbed to  an unforeseen gravity attack. So I am currently using it with an  external monitor, and am therefore unable to see anything at boot until  the Ubuntu splash screen appears. The next thing is the login screen (at  which point all is well), and as soon as I login, I lose keyboard and  mouse control (as well as mouse cursor), and the screen is frozen.

I've  tried CTRL-ALT-F2, etc., to switch to a TTY interface quickly after I  hit the login button, but when a TTY does open, it takes forever  (minutes), and responds very slowly, with messages spitting out at me  while I'm trying to type... and it never leads to anything.

Here's a snippet showing some of the messages:

hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x00170503
BUG: soft lockup - CPU#1 stuck for 24s! [kworker/1:1/103]
BUG: soft lockup - CPU#0 stuck for 25s! [jbd2/sdb5-8:176]
BUG: soft lockup - CPU#1 stuck for 21s! [kworker/1:1/103]
iwlwifi 0000:02:00.0: Microcode SW error detected. Restarting 0x12000000.
INFO: rcu_sched detected stalls on CPUs/tasks: {} (detected by 1, t=15256 jiffies, g=1581, c=1580, q=0)
INFO: Stall ended before state dump start

Anybody have an idea what could be causing this, or what to try next?

Thanks in advance!

-Mark

---

### Post by SuperFreak on 2014-07-05
What are the laptops specs?

---

### Post by mjpatey on 2014-07-05
It's a circa-2011 Sony VAIO Macbook Pro look-alike. The model number is VPC-Z11QGX/S. It has a quad-core 2.53 GHz Intel Core i7 processor with an nVidia video card of some sort. 4GB RAM, 2 internal SSDs, 128GB each. sda is the Windows 7 drive and sdb is where Ubuntu lives (currently all on one partition). Trying to run Ubuntu 14.04 64-bit edition.

Incidentally, at the moment I'm trying to cheat my way around it... will see how this goes. I've now installed Ubuntu 13.10, and it works perfectly so far (certainly no sign of the trouble 14.04 has been giving me). I have nothing of worth stored in the install, so I'm going to try simply upgrading to 14.04 from this 13.10 install, and see if it works.

Will post back in a bit!

---

### Post by ibexslam on 2014-07-06
I'm far from an expert, but I was having a similar problem, crashing...or should I say the screen locking up, and the display going funny...it turns out that changing the video driver to one for the envidia video card in  my hardware made the problem go away. You'd have to get to the settings before crashing...maybe there's another way. 

I.

---

### Post by mjpatey on 2014-07-06
Well, for now I'm settling on Ubuntu 13.10 without the proprietary nVidia driver. As soon as I try to install either version of the  proprietary driver, I lose xserver video. So I think I will hang back a bit and enjoy my working system. I'll check back in once Utopic is in beta.

Thanks!

---

