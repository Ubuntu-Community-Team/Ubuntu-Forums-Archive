---
title: "Problem with Xorg or AmaroK and 2GB RAM"
date: 2007-03-20
forum: General Help
---

### Post by Kalisandra on 2007-03-20
Hi, I have a problem:

My box has a AMD 64 3200+, nvidia 6600, and 1GB RAM and runs Xubuntu 6.10, 64-bit version. It's been running with this setup since edgy was released and functions fine.

I recently decided to add another 1GB of ram from an identical box built at the same time - the ram's  identical to that already in the machine - same batch even.

Now, with 2GB ram the system is very unstable, and when Amarok is running sooner or later Xorg suddenly munches 99.9% of the CPU time and I lose all control. The mouse still moves, but it's buttons are dead, as is the keyboard (can't even turn caps-lock on/off, change consoles, or use ctrl-alt-backspace to restart X). Amarok keeps playing, however. I set up a remote console on another machine and ran Top, which showed Xorg using almost all the CPU cycles (that's how I know it's Xorg). Killing AmaroK does not release the cpu, and once this happens xorg, xfce, and everything else x-windows related refuse to die from a 'kill' command.

Now, I'm pretty sure the 'new' ram is not at fault, because playing games under XP with the extra ram is trouble-free, and pullong the original ram and leaving the new ram in (so there's only 1GB) has returned the original stability (as does just reverting to the original ram only).

It's like AmaroK and/or Xorg can't handle the extra ram and just break.

Any ideas what the heck is going on?

BTW, I've got AmaroK 1.4.3 using KDE 3.5.5, and Xorg 7.1.1, if that's of any use.

---

### Post by somafm on 2007-03-20
Hello,

I had the cpu usage problem with Xorg a while back. It would happen randomly and I would have to restart, but then it would just come back later.

I fixed it by installing [**_Envy_**]("http://albertomilone.com/index.html") as recommended by another thread. Envy will basically detect your video card, install the latest/correct drivers, and configure your xorg.conf file properly.

That seemed to fix the problem considering I have not seen the high cpu usage again and the machine has been up for about a week now, and acting good.

I have been going around looking for people with a similar problem posting this info, so I hope it helps you like it helped me. Best of luck!

---

### Post by Kalisandra on 2007-03-21
Okay, I used Envy, and it *seems* to have solved problems with AmaroK. However, I now find I'm getting the problem others have reported of Xorg using all the cpu cycles if the box is left idle for an extended period. :(

I notice that many others reporting these problems also have 2GB RAM. I wonder if that's got something to do with it, or whether it simply shows that forum posters often have a couple of gigs of memory.

---

