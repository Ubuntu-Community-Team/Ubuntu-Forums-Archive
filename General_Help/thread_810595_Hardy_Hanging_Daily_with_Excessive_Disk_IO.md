---
title: "Hardy Hanging Daily with Excessive Disk I/O"
date: 2008-05-28
forum: General Help
---

### Post by Jamie Jackson on 2008-05-28
About once a day, my machine becomes unusable, and the only solution I have been able to come up with is a hard reset, which rules out saving my work, etc.

This started when I upgraded to Hardy (from Gutsy, where the problem didn't occur), and has persisted through the 2.6.24-17-generic kernel upgrade, which an update provided a day or two ago.

**System**
Ubuntu 8.04
Linux mercury 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux

**Apps I Run Nearly Full-Time**
Firefox, Eclipse, Evolution, and Pidgin.

**Hang Description**
I'm working (issue doesn't seem to have to do with which app's in the foreground), and I notice excessive I/O (HD light and HD physical access sounds). The I/O never stops for any significant length of time, and I've given it 15-20 minutes to settle down before hard-resetting it.

Once this starts, mouse movement lags by about 30 seconds or more, and mouse clicks no longer seem to trigger anything.

While the issue is occurring, keyboard input doesn't seem to do anything at all (I can't alt-tab, alt-F2, nor ctrl-alt-backspace).

**Things I've Tried**
I tried applying the Firefox 3 Beta 5 workaround (switching off the phishing filters). Further once I started Firefox, I found its pid, and ran "ionice -c3" against its pid. Therefore, I'm guessing Firefox is not the issue.

**Question**
Since I can't do anything once this starts, I need a plan for diagnosing the problem. Please let me know what to do.

Thanks,
Jamie

---

### Post by Jamie Jackson on 2008-05-28
Bump. I'm posting this from my phone, as my machine is rebooting after the second hang of the day...

---

### Post by prshah on 2008-05-29
> **Jamie Jackson said:**
> 
I'm working (issue doesn't seem to have to do with which app's in the foreground), and I notice excessive I/O (HD light and HD physical access sounds). The I/O never stops for any significant length of time, and I've given it 15-20 minutes to settle down before hard-resetting it.


Looks like a pure badblocks problem to me. Boot off a live CD, make sure your partitions are unmounted, then open a terminal (Applications-Accessories-Terminal) give the command ```
sudo badblocks -v /dev/sda
```, replace /dev/sda with your actual device. You should see a running count, and if any badblocks are detected, it will give the block number, drop a line, and continue.

Note that the default badblocks as given above is non-destructive to data, but certain switches will overwrite everything, so don't experiment! Also make sure all partitions on the device being checked are unmounted! 

If you have badblocks, post back for details on how to permanently disable them from being used.

---

### Post by Jamie Jackson on 2008-06-02
> **prshah said:**
> Looks like a pure badblocks problem to me. Boot off a live CD, make sure your partitions are unmounted, then open a terminal (Applications-Accessories-Terminal) give the command ```
sudo badblocks -v /dev/sda
```, replace /dev/sda with your actual device. You should see a running count, and if any badblocks are detected, it will give the block number, drop a line, and continue.

Note that the default badblocks as given above is non-destructive to data, but certain switches will overwrite everything, so don't experiment! Also make sure all partitions on the device being checked are unmounted! 

If you have badblocks, post back for details on how to permanently disable them from being used.

Is this more thorough/different than the disk check that Ubuntu performs periodically? I let that one run today, but haven't gotten a chance to run your command yet.

However, today, I was able to ctrl-alt-backspace today while the problem happened. I was able to log back in in a terminal, and found that wineserver was the one thrashing the disk. I'm not sure how to find out whether it was wineserver itself that has the problem, or whether one of the installed windows apps is to blame.

If anyone has any ideas as to how to diagnose this, let me know. I suspect I'll have to open a new thread though.

---

### Post by Jamie Jackson on 2008-06-02
I didn't manually upgrade Wine when I upgraded to Hardy, and it seems that I was [supposed to]("http://www.winehq.org/site/download-deb").

Hopefully, this will fix the issue.

---

### Post by Jamie Jackson on 2008-06-03
I installed the latest wine (wine-1.0-rc3), and I'm still having issues. I haven't figured out if it's wine itself misbehaving, or whether Internet Explorer (from IEs4Linux) is causing the problem, but I do know that's one, the other, or a combination of the two.

I set up a keyboard shortcut that runs a shell script (which, in turn, runs "killall IEXPLORE.EXE; killall wineserver;"), and this seems to solve the issue for me. It doesn't explain why wine goes nuts, but at least I don't think I'll have to reboot anymore to fix it.

---

### Post by brianafischer on 2008-07-01
I am having the same issues on my install Hardy 8.04 all updates installed.  I did a clean install of Hardy.  I do not have any wine applications running (but Wine is installed) at the time I have seen the disk thrashing.  The computer will not respond so I have no choice but to hard power off (very bad for the hard drive!).  Please let me know what information I should provide to help troubleshoot this issue.

---

### Post by Jamie Jackson on 2008-07-03
Well, it wouldn't hurt to set up a keystroke shortcut that runs the command I noted. I don't know whether it was a wine app or wine itself that caused the problem, but my shortcut has saved me, when I caught the thrashing in its early stages. I haven't seen the problem in a little while, though, and I think that maybe some of the latest wine updates I've seen come in have fixed the problem.

Still, I haven't removed the shortcut, just in case...

Oh, as I mentioned earlier, did you *manually* upgrade wine after upgrading to hardy? It seems you have to (per post number 5).

---

### Post by brianafischer on 2008-07-03
> **Jamie Jackson said:**
> Well, it wouldn't hurt to set up a keystroke shortcut that runs the command I noted. I don't know whether it was a wine app or wine itself that caused the problem, but my shortcut has saved me, when I caught the thrashing in its early stages. I haven't seen the problem in a little while, though, and I think that maybe some of the latest wine updates I've seen come in have fixed the problem.

Still, I haven't removed the shortcut, just in case...

Oh, as I mentioned earlier, did you *manually* upgrade wine after upgrading to hardy? It seems you have to (per post number 5).

I didn't upgrade to Hardy.  I did a clean install.

---

### Post by Jamie Jackson on 2008-07-03
> **brianafischer said:**
> I didn't upgrade to Hardy.  I did a clean install.

Mental note: I need to slow down when I read. ;)

The shortcut suggestion still stands, though. :)

---

### Post by brianafischer on 2008-07-08
> **Jamie Jackson said:**
> Mental note: I need to slow down when I read. ;)

The shortcut suggestion still stands, though. :)

I took this a step further and did an apt-get remove wine.  I will update if this made a difference.  How can I debug what is going on?  Should I take a look at some specific logs?  This is extremely frustrating!

---

### Post by Jamie Jackson on 2008-07-10
> **brianafischer said:**
> I took this a step further and did an apt-get remove wine.  I will update if this made a difference.  How can I debug what is going on?  Should I take a look at some specific logs?  This is extremely frustrating!

I also don't know how I would debug this (although it's moot for me now). The only way I was able to catch it was one time, I got lucky and was able to open the system monitor in time to see that wine (or iexplore) was going ape. That window of opportunity was impossibly short, though.

---

### Post by wayfarer_boy on 2008-09-23
I realise this may be an old topic, but I too have started to experience problems with wineserver and 100% disk activity on Hardy.  I only experienced it, however, once I ran ies4linux's ie6 app (I've been running wine apps for a while, so the offender seems to be this one).

I tried to kill the wineserver:
```
sudo killall -w -v wineserver
```
but killall just sat there, waiting for wineserver to die.

I've since purged my wine installation
```
sudo aptitude purge wine
```
and removed my ~/.wine and ~/.ies4linux folders.  I then followed the instructions as [linked in post #5]("http://www.winehq.org/site/download-deb") and reinstalled wine (not sure if I'd done these steps last time, but felt it was safer to do them all):
```
sudo aptitude update
sudo aptitude install wine
```
and reinstalled ies4linux.

I've been using ie6 for a good half hour now, and there seem to be no ill effects.  Also, ie6 loads very quickly now, so maybe I had some residual clutter from a previous gutsy installation somewhere in my .wine folder??

---

### Post by wayfarer_boy on 2008-10-08
I thought I should add that I've now found I can reproduce the 100% disk activity problem when running Firefox3 and ies4linux simultaneously.  I haven't delved into it, but will post more (and submit a bug) when I get an opportunity.

---

### Post by eheck on 2008-10-24
FWIW, I'm having the same problem and I don't even have wine installed.
I think, I will do the drive check.

---

### Post by uzzo2 on 2008-10-24
I am having the same problem with wineserver and IEs4linux, IE6 version. running "top" in the terminal shows me that wineserver is burning up my cpu driving up the temperature.

---

### Post by ju2wheels on 2008-10-24
I can definitely confirm this type of issues with IEs4Linux, I think it has a serious mem leak issue when run under wine for some reason. I stopped running IEs4Linux on my machine because it would chew up 100% of the processor until the machine was completely unresponsive [mind you that is a quad core 2.0ghz with 4gb of ram it manages to lock up]. 

I would recommend not running IEs4Linux as once its started its very difficult to actually kill wine properly if you leave it running too long and avoid having to reboot the entire machine. If you really need IE, I suggest VBox. It might be overkill just for IE but at least it wont render your machine unresponsive.

---

### Post by uzzo2 on 2008-10-24
> **ju2wheels said:**
> I can definitely confirm this type of issues with IEs4Linux, I think it has a serious mem leak issue when run under wine for some reason. I stopped running IEs4Linux on my machine because it would chew up 100% of the processor until the machine was completely unresponsive [mind you that is a quad core 2.0ghz with 4gb of ram it manages to lock up]. 

I would recommend not running IEs4Linux as once its started its very difficult to actually kill wine properly if you leave it running too long and avoid having to reboot the entire machine. If you really need IE, I suggest VBox. It might be overkill just for IE but at least it wont render your machine unresponsive.
yes i am thinking the same thing, i have my old xp box networked now so i can just use it. i only have one website that i have to go to every week that you can't use firefox for, it has to be IE.

---

### Post by eheck on 2008-10-27
Disk check completed here with no bad blocks, still no wine installed. Is there something else that might cause the identical symptoms?

---

### Post by samandiriel on 2008-11-19
Had similar issues using the latest ies4linux on Ubuntu 8.10 (Intrepid). For me, the start up script fix did the trick.

I also found several rogue explorer.exe processes as well as IEXPLORE and winserver. After killing all these, modifying the script as above, and running the modified script I had absolutely no problems.

It looks like the script's piping to the debug is fouling things up; perhaps this was left in accidentally by the author during development.

script fix (credit Marc Davignon) from [http://bugs.launchpad.net/ubuntu/+so...ne/+bug/205895](http://bugs.launchpad.net/ubuntu/+so...ne/+bug/205895)
---------------------------------------------------------------
1) cd $HOME/.ies4linux/bin
2) cp -av ie6 ie6.orig
3) Replaced the content of the ie6 file with:
#!/usr/bin/env bash
# IEs 4 Linux script to run ie6 - [http://tatanka.com.br/ies4linux](http://tatanka.com.br/ies4linux)

cd
export WINEPREFIX="$HOME/.ies4linux/ie6"

wine "$HOME/.ies4linux/ie6/drive_c/Program Files/Internet Explorer/IEXPLORE.EXE" "$@" >/dev/null 2>&1 &

---

