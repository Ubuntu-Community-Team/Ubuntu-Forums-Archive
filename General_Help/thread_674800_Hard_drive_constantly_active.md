---
title: "Hard drive constantly active"
date: 2008-01-22
forum: General Help
---

### Post by RawMustard on 2008-01-22
I've just done a fresh install of Gutsy 7.10 on a new Gigabyte GA-73PVM-S2H Mobo with 1 sata drive, a sata DVD and a core2 duo cpu.  I installed from the alt cd and did a command line system install, that's a base install to cli.  After that I installed xorg, gdm, fluxbox, menu, pmount, pcmanfm, leafpad and linux-backports-modules and rebooted.

So I get into my nice shiny new very light desktop and all is running sweet except every 2 to 2.5 seconds my hard drive light flickers.  It's a constant flicker un-ending after 3 hours of use and I can't for the life of me figure out what could be causing it.

I was hoping someone here might have a clue?

---

### Post by benzo8 on 2008-01-22
Almost certainly it's beagle and/or tracker indexing your hard drive for the Deskbar search functions. Search the forums for beagled and trackerd to find plenty of threads discussing their, er, dedication... :-)

---

### Post by RawMustard on 2008-01-22
I don't have either installed :(

---

### Post by dbera on 2008-01-22
Could be strigi for you ? Since you said Kubuntu which has strigi pre-installed.

**OFF Topic**

Previously it was beagle for all the computer problems. Then tracker joined the scene (more after 7.10 when it was installed by default). But now with users having the same problems with neither installed, the Ubuntu family has to look for a new software to take all the blames. Its easy when you have a soft target ... my sympathies are with the ubuntu users who are looking at the wrong place for their problems.

---

### Post by fyo on 2008-01-22
I don't think there's any tool that does this on Linux withouth CONFIG_TASK_IO_ACCOUNTING enabled in the kernel (on compile), which is unfortunately not the case with Gutsy (7.10).

Current Hardy builds reportedly has this enabled...

When enabled, there are several tools that will do the trick. A recent version of "pidstat" (in the "sysstat" package) and "atop" are two examples.

---

### Post by RawMustard on 2008-01-23
Thanks guys!
I guess I'll just have to put it down to another gutsy bug - Soooo many of them :(

---

### Post by RawMustard on 2008-01-24
OK so I've narrowed it down to hal, but I still can't stop it :(  I'd install Feisty on this beast, but it won't recognise a lot of the hardware and compiling kernels has never really worked out well for me :(  Guess I'll have to use another distro(bummer) till a fix comes along in the next version hopefully :(

---

### Post by TheExplorer on 2008-01-24
The original article is [here]("http://linuxhelp.blogspot.com/2007/10/problem-encountered-by-laptop-users.html") (thanks to RAVI):

A number of people are blogging about how running the latest version of Ubuntu Gutsy Gibbon on a laptop could possibly end up causing an early demise of the laptop hard disk. The problem is that the hard disk essentially consists of a spindle and a bunch of disks stacked one on top of the other which rotate at high speeds. Now as with all objects which have moving parts, hard disk also faces wear and tear. The problem faced by Ubuntu laptop users is the aggressive use of hard disk by Ubuntu thus shortening the life of the hard disk.

A bug submitted at launchpad confirms this anomaly. So what is the solution to this rather irritating problem ?

Use hdparm; a command line tool to disable advanced power management (APM). This is achieved by running the following command :

$ sudo hdparm -B 255 /dev/sda

Here the -B option is used to set the APM value. A low value means aggressive power management (that translates to more wear and tear for your hard disk) and a high value means better performance (but more battery consumption). By setting the value as 255, we have disabled the APM all together. Over 2 years back, I had written an article explaining how to improve your hard disk performance using hdparm. And if you are interested in knowing more about hdparm, you may read the article.

I run Ubuntu Gutsy Gibbon and it doesn't cause this problem on my desktop PC.

Check out the opinions from two sources [ linux hero and Planet Beranger ] to get a different angle.

---

### Post by RawMustard on 2008-01-24
Thanks, I've been reading all those posts all over the net.  Anyway, I tried running that command, but all I got was HDIO_Drive_CMD failed input/output error. My drive is on /dev/sda

But still,  I don't think that's my problem.  Having listened to my hard drive with a stethoscope, I "can't hear" the disks being accessed or changing speed.

Something else is causing the hd-led to light everything 2 seconds and it happens soon as I install hal.  Doing a fresh install to a command line base system with no other software installed, it doesn't happen.  Installing x and other apps, eveything is ok.  But soon as I install hal the hd-led lights without fail every 2 seconds and is un-ending :(

I tried installing Fedora to see if it was the same and it wasn't, so something in Ubuntu is causing this strange and annoying phenomenon.

---

### Post by TheExplorer on 2008-01-24
Look [here]("http://ubuntuforums.org/showthread.php?t=147586").
Also [here]("http://forums.slimdevices.com/showthread.php?t=39833") and maybe [here]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/32826").

---

### Post by joeliol on 2008-03-17
Ive had the same problem, where my hard drive was constantly 40-70% active. I tried all the laptop mode aggressive power saving stuff thats recommended everywhere, removed trackerd, beagle etc to no avail. The answer for me was to use "top" to find what was going on, which shows root processes that system monitor wont show. Anyway, it turned out to be MythTV backend. I just removed MythTV, which I never used and problem solved. 
Hope this helps somebody.

---

### Post by radioman1000 on 2008-05-02
Yep.  It was Myth-TV causing the hard drive LED to flash constantly.  Removed it and all is well.  Thanks joeliol.

---

### Post by Mitch_Arsenal on 2008-05-23
Thanks for the solution. Been having the same problem and it was starting to frustrate me. Definitely MythTV.

---

