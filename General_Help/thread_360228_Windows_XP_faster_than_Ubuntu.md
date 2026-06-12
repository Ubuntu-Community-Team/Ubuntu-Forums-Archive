---
title: "Windows XP faster than Ubuntu?"
date: 2007-02-12
forum: General Help
---

### Post by ZeldaFan on 2007-02-12
I am running an HP dv9000t with these configurations:
17" screen (1650 x 1050 resolution)
Core 2 Duo T5600 (1.83 ghz)
2 GB RAM at 667 MHz
100 GB hard drive space
Windows Media Center Edition installed at the moment
512 MB Nvidia GeForce go 7600 GPU
Analog TV tuner
intel 3945 a/b/g internal wireless and bluetooth
dvd-rw drive w/ lightscribe

I dual-boot windows XP and Ubuntu edgy eft, but I have noticed that in many cases that Windows XP operates faster than Ubuntu. One of the biggest problems is the booting time, as Windows XP loads relatively quickly, while Ubuntu gets stuck loading one think for like at least 2 to 3 minutes before finishing completely loading. I have no idea what it is that is loading, because I only see that bar that indicates the loading progress. Also, on Ubuntu, I installed beryl and my system responsiveness is noticeable slower than Windows XP's. Even when I am running widgets on Windows XP, it runs faster than Ubuntu. However, it is weird, because when I run windows, it uses around 400 mb of RAM at least, while Ubuntu only uses 350 MB when running beryl. So, shouldn't Ubuntu be more responsive in that case, because for example when browsing certain websites, the responsiveness of the UI, in which I am scrolling through a website or something is a little bit slower. After all, I don't want to have to abandon Ubuntu in favor of XP for its speed of all things. Is there a possibility that some of my system's resources are not being fully utilized, like my GPU, CPU, or RAM (I know, though, that Ubuntu recognizes both of laptop's cores for the CPU).

---

### Post by llamakc on 2007-02-12
Install the package bootchart and figure out where it is 'slowing down' at; or boot without the bootsplash and figure out what is creating your bottleneck. Meanwhile, use a stopwatch to time Windows for comparison.

You can't  compare Beryl (which is still heavily developed) on Ubuntu with Windows that does not run Beryl. 

Without sharing which websites you notice lag at there is no way to evaluate your claim. 

Are you using NVidia's drivers?

---

### Post by banditti on 2007-02-12
If you want to get a feel for what Ubuntu is doing behind the splash:

Remove both "quiet" and "splash" options from the kernel entry in /boot/grub/menu.lst


Do you think your drivers are good to go?

---

### Post by ZeldaFan on 2007-02-12
Well, the websites I am referring to are ones that use heavy plugins, like [www.nba.com](www.nba.com), [www.espn.com](www.espn.com), and [www.cnet.com](www.cnet.com). Also, I am using Nvidia drivers following some howto guide to installing nvidia's drivers and they apparently work, because the splash screen appears in the beginning and I can change the settings. And with or without Beryl, if my CPU usage is essentially the same on both OS's and if I use less RAM on Ubuntu, shouldn't it technically run faster anyway? Are there some Nvidia drivers that work better than others? I am an absolute beginner to Ubuntu and edgy eft by the way.

---

### Post by highneko on 2007-02-12
> **banditti said:**
> If you want to get a feel for what Ubuntu is doing behind the splash:

Remove both "quiet" and "splash" options from the kernel entry in /boot/grub/menu.lst


Do you think your drivers are good to go?

I never knew that. I just tried it for fun to see what it would look like. It actually seems faster just by removing the boring splash stuff. Maybe it's the fast movement of the scrolling text. It gives the feeling of a faster boot. Thanks for the info.

---

### Post by nickoli_02 on 2007-02-12
Your partitions are probably being checked for errors during the boot process, making it noticably slower than it should be. You can disable the fsck in /etc/fstab doing this:

```
sudo nano -b /etc/fstab
```

the -b option creates a backup of the file. Now replace the entries with '1' as the last digit in the row with '0'. This should work. If anything goes wrong when your reboot, restore the backup file.

---

### Post by ZeldaFan on 2007-02-12
Any thoughts why my computer is going slower with Beryl though?

---

### Post by jml on 2007-02-12
Beryl will slow down your system for several possible reasons.  First, as someone already pointed out.  Beryl is a project still under heavy developement.  In other words, the code has not yet been totally optimized.  In Windows terms, its not yet at a version 1.0 level yet.  So as time goes on, it should improve.

Second, by its very design, Beryl is extremely resource intensive.  Generating all of that eye candy and 3D effects uses a lot of resources.  As to why Ubuntu uses less system ram than Windows, I would conjecture that it is because it is relying on the video card's vram to draw the screens.  Even with an accelerated graphics card, most people notice a difference when Beryl is running.  Not unlike trying to run a high end PC game with all of the graphics turned up to the max.  This is not a "fault" of Unbuntu, but a fact of life. 

Joe

---

### Post by allwin on 2007-02-12
Here's a few geekly things you can try:

[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

Also, I would suggest you do a GOOGLE for how to use HDPARM to set your disks in DMA mode for speedier access.  Try doing a "sudo hdparm -tT /dev/hda" and see what kind of throughput you are getting.  If it's anemic, you can turn DMA on, set it into 32 bit mode, etc.

I have a 550 MHZ Pentium clunker and it amazes me how fast it is even with Beryl running after it's been tweaked up.  I also note that KDE is pokier all the way around compared to GNOME, particularly it takes longer to launch things, or so it seems, than GNOME.

You might want to check your SYSTEM LOG to see if there is some process kicking out a lot of error messages over and over.  That can sap the power.  I see a lot of people complaining about things being slow or slowing down for no good reason, and I always ask myself if there isn't some task logging like crazy which could be fixed.

IMHO, the desktop (GNOME or whatever) plus the X server which provides the graphics framework are overall a little slower than XP because they are layers stacked upon the invisible parts of the OS.  If you fiddle with a program called "gconf-editor" for GNOME, you can also find a setting in there called "reduced resources", which if turned on makes things a little more responsive.

Using XFCE as a desktop also adds a lot of speed compared to GNOME and KDE.  Eventually I got things so I would say XP and my own installation are on a par with each other.  The tweaks add up.

Strangely, if you google around, you can find Internet Explorer 6 packaged up with WINE, so that the native code runs...and IMHO it seems a little zippier than Firefox all the way around (but lacks ad blockers and popup blockers).  I think the search term is IE4LINUX.

It seems to me the policy of Linux in general is, after install, to configure your hardware for SAFE (but not necessarily OPTIMUM) usage.  Hence it might not turn DMA on or 32 bit mode at first.  Kind of like going back in time to 1995 hardware in some cases.  But it's easy enough to change.

Just like with XP, there are also a lot of things automatically started which you probably will never use, which contribute to longer log in and reboot times.  Plus there are CRON tasks that kick off to do things like archive and roll the system log, run indexers if you have them turned on, etc.  Personally I haven't looked into this for further tweaking myself.

Beryl doesn't necessarily slow things down, either.  It does have to start up at log in which takes some time, but after that, it's not much of a load.

---

### Post by banditti on 2007-02-13
You are welcome highneko.  kinda cool.

---

### Post by Levander on 2007-03-15
I remember being told maybe a year ago in #web on Freenode that Firefox on Windows is slower than Firefox on Linux for web pages that have background images that have to be scrolled when the page is scrolled.  At the time those background images were redrawn every time the web page was moved up or down on Linux, but the image was cached and didn't have to be redrawn from scratch on Windows.  It was just a matter of Firefox not being as optimized for Linux as it is for Windows.

That was a year ago though, maybe it's changed.  Although I vaguely remember seeing that effect on a web page not long ago.  

For web developers this is a reason not to make those background images that repeat themselves across the background too small.  I first saw this effect when I had a 1 pixel wide image that was being repeated all the way across the background horizontally.  Making the image 25 pixels wide sped up scrolling immensely.  Even clueless users would have noticed a big difference.

---

