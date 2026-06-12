---
title: "Possible Memory Leak?"
date: 2007-03-27
forum: General Help
---

### Post by Yellow Onion on 2007-03-27
when I turn on my computer my memory usage is at bout 260 MiB
I leave my computer on all day/night for bout 4 days and now my memory is at 600 MiB usage
so i pull up my system monitor and notice that gnome-panel is using 100 MiB of memory (10 MiB after boot) it had also been crashing every now and then since the update. I also noticed that at-spi-registryd is 25MiBs (2 MiB after boot) dont know what else is getting bigger but there must be more
and also i couldnt log back in to gdm after hitting ctrl+alt+backspace it would just sit there with the orange background also tried with startx same thing happened but after reboot i can login fine

---

### Post by m83 on 2007-03-27
Maybe you have physical problems with your memory modules. Run a memtest86 and see if you have any errors.

---

### Post by Yellow Onion on 2007-03-30
Worth a try I'll get around to do it soon

---

### Post by Eric Layne on 2007-04-26
I am having the same problem. Gnome-panel chews up memory as the computer sits idle, so after about 24 hours the system is extremely sluggish. Note this is on a fresh install of Feisty, *after* the initial software update.

---

### Post by tgalati4 on 2007-04-26
This may be normal behavior.  Linux will quickly use 90% of the RAM and start sending pages to cache.  The gnome-panel simply gobbles memory for all of those desktops and windows that are open.  You can:

killall gnome-panel

to reset it, or control-alt-backspace to bring down the xserver and start fresh.

The slowness could be due to a lack of adequate swap space.

Report the results of:

vmstat

Pay attention to the "si" and "so" statistics.  That's swap in and swap out.  If swap in is high then you will experience slowdowns.  Swap out is OK as old memory pages get sent out to swap for retrieval later (possibly never).  Swap-in however will slow a computer down quite a bit depending on how often pages have to be called in.

What is the RAM on these systems?  How large is the swap disk?

man vmstat

will give you several options.  You can run it often, you can capture results to a file:

vmstat > mymemoryresultsonmyreallyslowsystem.txt

You can compare results shortly after boot and after several days of running.

RAM is your friend.  Ubuntu likes a minimum of 256 MB, 512 is better.  1 GB is styling.

---

### Post by Yellow Onion on 2007-04-27
1GiB of RAM and Dont think i had swap but now i have 1GiB of it mine didn't get sluggish just starts crashing,

Ill leave my computer on over the next couple of days try running with feisty and see what happens (tried downgrading to the old edgy version and didnt seem to have the same problem but had to upgrade to update to feisty.

still haven't got around to do test but windows (x64) seams to run fine for 4 days straight (then BSOD after playing Day of Defeat: Source).

Also if i was to kill X server (clt+alt+bckspc) i was unable to log back in, screen just went orange as normal but didn't show the loading bar and nothing happened so i had to restart

---

### Post by blamecanada on 2007-04-27
My laptop has 512mb of memory (around 495 after the graphics are done with it), and after about 400 megs are used the system really starts to slow down.

---

### Post by tgalati4 on 2007-04-28
I'm still running Dapper 6.06.1 and my memory is filled to 95% most of the time, but my machines are snappy and I can recover from Xserver restarts.  My machines are up for several months at a time, so if there was an application problem, it would show up.  

As I am seeing more memory-related posts pop up on the forums, it looks like it may be a Gnome/xserver issue.  The inability to restart the xserver is troubling.

There are several good memory profiling tools out there.  We need to track down the specific application that is causing the leak.

---

### Post by Yellow Onion on 2007-04-30
Well I've been running Computer For a we while Gnome-panel hasn't Crashed But Its using 388MB of memory
Also Noticed that since the feisty Update Xorg is running twice, killed panel now is using 5.7MB

---

### Post by MarkDennehy on 2007-06-20
1Gb of RAM here, and Xorg is eating 342Mb of it to run one firefox window and one konqueror window. Now, granted, I'm running a three-screen xinerama setup, but that shouldn't eat *that* much memory, right?

---

### Post by Yellow Onion on 2007-07-13
Im not an expert but I wouldn't think so

---

