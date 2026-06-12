---
title: "Strange video problem - botched update?"
date: 2015-09-28
forum: General Help
---

### Post by WB0HYQ on 2015-09-28
My install of Ubuntu 14.04 has been running smoothly for months now on my HP G60 laptop, but three days ago the video suddenly began "tearing" with squares of video jumping around the upper third of the screen. It did this for about a minute and then the screen froze and the computer was unresponsive. Subsequent restarts did the same thing over and over. If I hold off trying to open ANY window, the freezing holds off for just a bit, but then starts after around 2-3 minutes. As soon as I open any window, the screen scrambles and the computer locks up.

I thought at first, I had some hardware problem, but that proved not to be true as I put the Distribution DVD in the drive and ran off it for two hours with no problem.

In troubleshooting, I noticed that the Nvidia Logo splash screen popped up briefly during bootup. It has NEVER done that before this problem started. I suspect that somehow an Nvidia driver has become enmeshed with the normal X-Driver (or whatever the stock driver is - I have not changed it from the original install).

Since the Distro-DVD runs fine, is there a way to re-install Ubuntu that will NOT destroy what I already have on the HD? Can I reinstall just the video drivers? 

If I am fast enough, I can manage to get a full-screen terminal window using Alt-F2. When I do that, the computer runs normally (and I am connected to my wireless AP here in the house). This makes me think there might be some command-line invocations I can make that will get/apply the default video drivers instead of having to completely reinstall Ubuntu. I'd like to avoid that if possible.

I can probably give more information, but don't know what would be useful at this time.

Bill

---

### Post by WB0HYQ on 2015-09-28
One thing that has started happening to my terminal mode is that every 50 seconds, I get interrupted with this:

```

[   53.795031] sd 4:0:0:0: [sdb] asking for cache data failed
[   53.795126] sd 4:0:0:0: [sdb] assuming drive cache: write through

```

This will repeat over and over again (with the time numbers changing, of course) and manage to break up any command line I try to enter. It is some sort of error for my drive, but I'm stumped as to what it means and how to get rid of it.

Isn't sda the primary drive? if so, then I haven't a clue what the computer thinks is sdb. I have no USB drive hooked up (although I use one every day). I think it may have been attached when the computer originally crashed and I had to hard-power it off. Could this be the system trying to re-attach the non-existing drive?

I'm out of my depth here. Help!!!

More:

The output of this command: sudo lshw -C video

Gives me this:

```

*-display
   description: vga compatible controller
   product: C77 [GeForce 8200M G]
   Vendor: Nvidia
   Physical ID: 0
   Bus Info: pci@0000:02:00.0
   Version: a2
   width: 64-bits
   Clock: 33Mhz
   Capabilities: pm msi vga_controller bus_master cap_list rom
   Config: driver=nvidia latency=0
   Resources: irq: 42 memory: c1000000-c1ffffff memory: d0000000-dfffffff memory: c4000000-c5ffffff ioport: 4000 (size=128) memory c6000000-c601ffff


```

Bill

---

### Post by ajgreeny on 2015-09-28
I have no idea if there has been a recent update of the nvidia driver recently but you can probably see if one turned up recently by running the command ```
grep -iw upgrade /var/log/dpkg.log.1 /var/log/dpkg.log | grep nvidia
```which will show you any nvidia package upgraded recently.

That may at least give you a clue about any changes that have been made to your graphics software and allow you to look for any possible driver change that may be available for that card by going to Additional Drivers and letting that search.

---

### Post by WB0HYQ on 2015-09-28
Thanks for the response. That command only results in displaying the upgrade I did a couple of hours ago by running:

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get disp-upgrade

The point being that ANY attempt to open a window after logging in normally will cause this screen to tear and freeze the computer. Thus, it is impossible to get to the System/software and updates Additional Drivers tab.

Do you happen to know the command line command that will replace ANY DRIVERS I have previously installed with the drivers that come with the distribution DVD?

Bill

---

### Post by ajgreeny on 2015-09-28
But did it show any output lines, ie any nvidia packages that were upgraded recently, and if si did it coincide with when this problem started?

To remove all nvidia drivers you could try command ```
sudo apt-get remove nvidia*
``` in terminal which should remove any nvidia driver you have installed at the moment.  You can do this from a command line if you can't get a stable desktop to run properly.  Use Ctrl+Alt+F1 to get a tty command line and login with username and password (password will not show).  Now reboot with ```
sudo shutdown -r now
```
You may have to use the nomodeset boot option with the open source driver but let's see what happens.

---

### Post by WB0HYQ on 2015-09-28
I have been using the TTY terminal all along to enter all these commands because the main GUI won't run more than a couple of minutes at best - and that is if I don't open anything that causes a window to appear. Firefox especially causes the system crash almost immediately after telling me Firefox crashed.

I'll give the apt-get remove nvidia* command and see what that produces.

Bill

---

### Post by WB0HYQ on 2015-09-28
Well,that certainly seems to have cleared up the problem, AJ. I've been running now for over ten minutes with NO flashes, glitches, or tearing of the display. In fact, I'm on Firefox now reporting this to you.

I had a feeling that somehow an Nvidia driver got caught up in a general "update" and caused the crashing. I will have to be a lot more selective in what I allow to update in the future.

According to "System/Details", I'm running Gallium 0.4 on NVAA. and "Additional Drivers" says I am using X.Org X server - Nouveau display driver

Seems to be working just fine. If this continues for, say, an hour, I will mark this 'Solved'.

Bill

---

### Post by Geoffrey_Arndt on 2015-09-28
And, when ready for a new machine, if using an all Intel system (both graphics and wireless) . . . then no issues like this anymore.    Only reason not to go this route is for serious gamers  . . .(imho).

---

### Post by WB0HYQ on 2015-09-28
Not quite sure what you mean, Geoffrey. There is nothing wrong with Nvidia for video, wireless, or anything else. An update just got caught crosswise, and messed up the system drivers. That could happen to ANY brand of device. I've got over 50 years of recycling computers and software. But then, even my cars tend to be run for long periods of time - like 357K miles on my VW camper before I retired it. I doubt I will be ready for a new laptop unless this one simply blows up. :D

Thanks for stopping by.

Bill

---

### Post by Geoffrey_Arndt on 2015-09-29
Hi WB0HYQ . . . you're right in many cases, but it is an extra unneeded level of complexity to run either nvidia or amd/ati graphics compared to Intel.  (see all the posts about nomodeset and/or building wireless drivers, and/or using external usb wifi adapters or kernel updates breaking the manually built drivers).    There's just more chances for error for the new or uninformed user - - and Intel basically makes this a non-issue.   If needing top end graphics, it's a trade-off many are willing to do.   For me, I'm more than satisfied with Intel graphics especially IrisPro 5200 and above.    So, I'm not knocking nvidia (as Linus has) . . . but if I can go with Open Source at acceptable performance, well, it's a win-win for how I use my laptops and desktop.

---

### Post by WB0HYQ on 2015-09-29
What you say is absolutely true, Geoffrey, but I have two different games that I run on my dual-boot Windows/Ubuntu machine that will not run properly (poor anti-aliasing and color control) on anything but my Nvidia graphics card. But, then, that's Windows-oriented. However, when I boot up Ubuntu, the graphics card comes along for the ride and I'm stuck with it. Unless I attempt to write my own driver, Linux dev's will never be able to match the Nvidia drivers because of proprietary issues (which is a shame, actually). This gaming computer (a high-end desktop) is wired into my home LAN and not wireless so there is one item that the laptop has to deal with.

If I do ever replace the laptop, then I will definitely take care with the specs and make sure that sound/graphics/video are all of the same manufacturer - whatever the make. The laptop is Linux only, and in use only when I take business trips, so Thunderbird/Firefox are prime, with OE Writer and Spreadsheet running a close second. No games, so the graphics don't have to be so rigidly controlled.

Bill

---

### Post by Geoffrey_Arndt on 2015-09-29
[URL="https://system76.com/desktops/leopard"]https://system76.com/desktops/leopard

Even better:

[https://system76.com/desktops/silverback](https://system76.com/desktops/silverback)




[/URL]

---

