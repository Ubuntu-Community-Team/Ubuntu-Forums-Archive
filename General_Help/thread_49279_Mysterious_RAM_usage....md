---
title: "Mysterious RAM usage..."
date: 2005-07-15
forum: General Help
---

### Post by spacemonkey on 2005-07-15
I've got a gig of ram installed in my box, and when I first boot my machine, and launch the programs that I usually have running, it takes about 20-25% of my ram.  After leaving my computer idle for a while, say, going to bed and checking it in the morning...the ram usage is up to around 50%.  That's not cached stuff either, I understand that caching fills up all the ram, but top reports that about 50% is used, and about 50% is cached.  I don't understand where my ram is going.  It's not really causing any problems with the computer, I'm just curious.  Of the percentages listed in top, the biggest memory hog is using 10%, max, and if you total all the processes listed, it only adds up to about 25% of the total ram.  Where is the other 25% going?  What is using it?  Do I have some sort of memory leak somewhere?

---

### Post by Lunde on 2005-07-15
[QUOTE=spacemonkey]I've got a gig of ram installed in my box, and when I first boot my machine, and launch the programs that I usually have running, it takes about 20-25% of my ram.  After leaving my computer idle for a while, say, going to bed and checking it in the morning...the ram usage is up to around 50%.  That's not cached stuff either, I understand that caching fills up all the ram, but top reports that about 50% is used, and about 50% is cached.  I don't understand where my ram is going.  It's not really causing any problems with the computer, I'm just curious.  Of the percentages listed in top, the biggest memory hog is using 10%, max, and if you total all the processes listed, it only adds up to about 25% of the total ram.  Where is the other 25% going?  What is using it?  Do I have some sort of memory leak somewhere?[/QUOTE]
 Yes there may be a memory leak, to help we need to know which programs you are running. Have you checked the **Applications -> System Tools -> System Monitor** then click on **Processes** and sort by **VM Size**

Which apps are taking up the memory? and how much?

I used to have a similuar problem but now my system is pretty stabile around 115 - 180MB (Swap & Memory combined) over night. Do you run any special cron jobs at night time?

---

### Post by spacemonkey on 2005-07-15
The only cron job that ever ran on this particular box was an auto-update script when it was running warty, but I removed it when I upgraded to hoary.  In top, the main memory hogs (in the %MEM column) are python at 11% (gdesklets), and Xorg at 4.8%, there are a few more that are around 1%, but not enough to justify a 50% ram usage.

In the System Monitor however, under the VM Size column, the top one is python, at 165.1MB, then firefox (which is closed if I'm not at the PC) at 81.3MB, then Nautilus at 40.9, evolution-data-server-1.2 at 38.3, clock-applet 34.5, etc.....But the thing that is strange to me is that for gdm, the VM size is 9.9 MB, but inside that is another gdm, 10.2 MB, then inside that is X, vm size 309 MB.  Could that be the problem?

---

### Post by Lunde on 2005-07-15
[QUOTE=spacemonkey]The only cron job that ever ran on this particular box was an auto-update script when it was running warty, but I removed it when I upgraded to hoary.  In top, the main memory hogs (in the %MEM column) are python at 11% (gdesklets), and Xorg at 4.8%, there are a few more that are around 1%, but not enough to justify a 50% ram usage.

In the System Monitor however, under the VM Size column, the top one is python, at 165.1MB, then firefox (which is closed if I'm not at the PC) at 81.3MB, then Nautilus at 40.9, evolution-data-server-1.2 at 38.3, clock-applet 34.5, etc.....But the thing that is strange to me is that for gdm, the VM size is 9.9 MB, but inside that is another gdm, 10.2 MB, then inside that is X, vm size 309 MB.  Could that be the problem?[/QUOTE]
 Firefox memory leak
[http://www.freerepublic.com/focus/f-bloggers/1327586/posts](http://www.freerepublic.com/focus/f-bloggers/1327586/posts)

Hmm, This is what I have: gdm, 9.9MB, gdm 10.2MB, X 165MB 
That may be some of the problem, dont know how to fix that. Do you have a special Graphic card? and is there something wrong with your drivers? 

What sort of desklets are you running?, google them for memory leaks

Also check further down the list to see if you have multiple processes of something running

---

### Post by spacemonkey on 2005-07-15
I did the firefox fix, gave myself 32MB of cache.  I'm using an Nvidia Geforce FX 5600, with the latest 7667 driver (latest from Nvidia, not Ubuntu repos).  As for desklets, I'm running two news grab desklets, sidecandy desklets, iweather, and starterbar.  I'll check google for any memory leaks in those.


[EDIT]
I found on the gdesklets forum that there are some leaks with gdesklets that are apparently ubuntu specific problems.  They said that the biggest problem was a leak librsvg, which is used by some desklets.  Any idea what desklets might use librsvg?  What exactly does librsvg do?

---

### Post by Lunde on 2005-07-16
[QUOTE=spacemonkey]I did the firefox fix, gave myself 32MB of cache.  I'm using an Nvidia Geforce FX 5600, with the latest 7667 driver (latest from Nvidia, not Ubuntu repos).  As for desklets, I'm running two news grab desklets, sidecandy desklets, iweather, and starterbar.  I'll check google for any memory leaks in those.


[EDIT]
I found on the gdesklets forum that there are some leaks with gdesklets that are apparently ubuntu specific problems.  They said that the biggest problem was a leak librsvg, which is used by some desklets.  Any idea what desklets might use librsvg?  What exactly does librsvg do?[/QUOTE]
 I tried the nvidia drivers 7667(4) myself and there are a lot of issues, don't know if they can cause anything like this. Probably not.. But check your frame rate in the glxgears after a fresh boot (leave the machine off for 10-15min cooling off), then after 5min running the glx frame rate "MAY" drop drastic. There were so much trouble for me with those drivers that I ripped them out fast. 

As for the librsvg, it's as I understand it's a part of gnome desktop
SAX-based renderer library for SVG files.
[http://librsvg.sourceforge.net/](http://librsvg.sourceforge.net/)
[http://sourceforge.net/mailarchive/forum.php?thread_id=5362799&forum_id=12476](http://sourceforge.net/mailarchive/forum.php?thread_id=5362799&forum_id=12476)

Try to remove the desklets from the startup and see if that is a part of the problem

---

### Post by spacemonkey on 2005-07-16
My computer has been running since last night without gdesklets running, and ram usage is up to about 42%.  So obviously gdesklets is not the issue, atleast not the biggest one.  There must be a leak elsewhere.

As for the 7667 drivers, I've read about the issues people have been having with this driver, but I can luckily say that none of them have affected me.  glxgears runs with a reasonable framerate at any time, and the games I usually play work great.

So if it's not gdesklets, what could it be?  The only other things that run all the time are gaim, firestarter, and Eterm.

---

### Post by Lunde on 2005-07-16
[QUOTE=spacemonkey]My computer has been running since last night without gdesklets running, and ram usage is up to about 42%.  So obviously gdesklets is not the issue, atleast not the biggest one.  There must be a leak elsewhere.

As for the 7667 drivers, I've read about the issues people have been having with this driver, but I can luckily say that none of them have affected me.  glxgears runs with a reasonable framerate at any time, and the games I usually play work great.

So if it's not gdesklets, what could it be?  The only other things that run all the time are gaim, firestarter, and Eterm.[/QUOTE]
 It does not have to be a program you run all the time, but here's a tool for checking the programs:
[http://www.gnome.org/projects/memprof/](http://www.gnome.org/projects/memprof/)

This is also available through synaptics:
$ sudo apt-get install memprof
$ killall gnome-panel

Gnome menu: Applications -> Programming -> Memory profiler

---

### Post by Lunde on 2005-07-16
[QUOTE=Lunde]It does not have to be a program you run all the time, but here's a tool for checking the programs:
[http://www.gnome.org/projects/memprof/](http://www.gnome.org/projects/memprof/)

This is also available through synaptics:
$ sudo apt-get install memprof
$ killall gnome-panel

Gnome menu: Applications -> Programming -> Memory profiler[/QUOTE]

Messed around with it a bit, not sure if it will help you much..

---

### Post by spacemonkey on 2005-07-17
Thanks, i'll gve it a shot and see if it helps.

---

### Post by spacemonkey on 2005-07-27
An update on my situation:

I lost one of my monitors for about a week, so I stopped using gdesklets with one monitor (just to cluttered).  I monitored my ram usage over that week, and I don't think it ever went over 20%, that's running everything I normally do except for gdesklets.  I got my new monitor in, and started gdesklets again.  Ram usage is up to 48%.  I'll do some more tests to see if i can figure out if its a specific desklet, or the whole thing.

---

### Post by ahallubuntu on 2005-07-29
I don't know if my problem is related or not, but I built a Ubuntu server a few weeks ago and it has been crashing.  I think I've figured out why:  vino-server (Gnome I take it) when I observed it grew to hundreds of MB (400MB+) and had already eaten half my swap space.  I restarted gdm and everything is fine now, but I'm assuming this will happen again while I'm not watching.

This server is a Samba file/print server.  It does not have a monitor/keyboard but I have set it up to login the main user at boot and login to Gnome, and I connect to it via VNC to monitor it.  No one is doing anything in Gnome except me with VNC.  Otherwise, people are accessing files and printing - that's it.

I haven't noticed anything routinely going wrong.  The server will run for days and use all 512MB of RAM and perhaps swap a little (I understand this is normal for Debian) with actually memory usage bouncing around a bit as it gets freed up on the fly.  Only suddenly did this one observed run-away memory hog start up.

Anyone have any insight into this?  Why might vino-server start running away like this all of the sudden when no one is using the GUI directly?  I installed the memory leak tool someone else posted but it's not yet clear how I could use it to debug this problem.  I've done all relevant updates (I'm using Hoary Hedgehog).  Can I try to install a newer version of Gnome?

Thanks!
Andrew

---

