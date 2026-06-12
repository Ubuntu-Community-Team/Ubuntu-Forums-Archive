---
title: "Ubuntu 7.10 freeze"
date: 2007-11-09
forum: General Help
---

### Post by nuno.santos on 2007-11-09
Hi. I'm having a freezing problem with Ubuntu 7.10. I have a default instalation and the system is freezing since the first time. Sometimes it takes just a couple of minutes but other times it happens after one or two hours. It happens when i run any applications but the system also freeze if i don't open any application. The only solution when it freeze is a reboot.

This problem happens also when i tried the Ubuntu 7.04, with same symptom. The only version that didn't freeze is Ubuntu 6.10, that works perfectly.

I have a Celeron 900Mhz, with a NVidia Geforce2 MX200 and 1Gb of RAM.

Can you help me trace the origin of the freezing? Thanks.

---

### Post by gsiliceo on 2007-11-09
Maybe you dont have to reboot, have you tried ctrl+alt+backspace? is a nice way to restart x.

---

### Post by DJMonoF on 2007-11-09
I am having the same problem here.  Gnome is frozen where any inputs from my keyboard and mouse dont register.  The weirdest part is that I can still move the cursor of my mouse.

Anyhelp welcome?

---

### Post by Bunjin on 2007-11-09
I have the same problem. I am trying to find a way to kill processes like in windows where you use the task manager. Any one know if there is a similar tool in ubuntu? Mostly I am using music players and they often crash my system. Audacious seems to be the best - affected by other program crashes but not causing any it'self. Dosen't seem to matter if I am running compiz fusion or not.

---

### Post by nuno.santos on 2007-11-10
> **gsiliceo said:**
> Maybe you dont have to reboot, have you tried ctrl+alt+backspace? is a nice way to restart x.

When it freezes, nothing works. The keyboard and the mouse stop.
Thanks.

---

### Post by FuturePilot on 2007-11-10
Try disabling powernowd. System>Administration>Services.
Uncheck CPU Frequency Manager (powernowd)
Reboot and see if that stops it.

---

### Post by ffi on 2007-11-10
if you have compiz(-fusion)/beryl installed, disable the screensaver (disable compiz first, then disable the screensaver and re-enable compiz)

---

### Post by cmost on 2007-11-10
Are you running the official nvidia driver (either self-compiled or from the restricted modules) or the generic nv / vesa driver?  If it's the former, try switching to the latter and see if that stops the freezing issues.  I had major freezing problems and finally (after months of tedious hardware testing) pinned it down to the latest version of the official nvidia driver.  This went away altogether when I downgraded to an older version of the nvidia driver.  Nvidia's new drivers suck apparently.  I hope this information is helpful.

---

### Post by LegoAddict on 2007-11-11
CTRL At backspace...  I'll have to try that.  I have the same problem.  Like a poster above, my mouse still works and I presume my keyboard works as well.  I had no problem like this under Feisty...

---

### Post by nuno.santos on 2007-11-11
> **FuturePilot said:**
> Try disabling powernowd. System>Administration>Services.
Uncheck CPU Frequency Manager (powernowd)
Reboot and see if that stops it.

I try it but didn't solved the freeze problem. Thanks anyway.

---

### Post by nuno.santos on 2007-11-11
> **ffi said:**
> if you have compiz(-fusion)/beryl installed, disable the screensaver (disable compiz first, then disable the screensaver and re-enable compiz)

I try it but didn't solved the freeze problem. Thanks anyway.

---

### Post by Pbethe on 2007-11-11
I have been playing around with Ubuntu for a while now, trying the live CD.  I always get the some problem, the system becomes unresponsive.  The mouse will move the pointer, but nothing happens when I click.  This has happened with 6.06 and 7.04.  This old machine has a 556 MHz Celeron and 384 M of memory.  Thinking that I just don't have enough computing power, I now have a Xubuntu 7.10 CD.  Same problem, all I can do is reset or push the power button.

---

### Post by gsiliceo on 2007-11-11
happens, linux sux

---

### Post by cmost on 2007-11-12
> **gsiliceo said:**
> happens, linux sux

To say "Linux sux" is to say the Kernel sux and nothing could be further from the truth.  What you're referring to as simply "Linux" is really a very large collection of software associated with the Linux kernel proper, hence the term "distribution".  Very likely, the problem with Ubuntu freezing has something to do with one of these associated programs and nothing at all to do with the Linux kernel itself.  When you consider that there are nearly 400 distributions but only this one is freezing, then it becomes apparent that's the case.  If you're using Ubuntu and it's freezing for you and you have verified there is no problem with your hardware (i.e., RAM, hard disk, cooling, graphics card, etc.) then switch distributions.  While Ubuntu aims to work well on the average hardware, it can't possibly work flawlessly on every single system.  Especially since hardware vendors fail to supply drivers themselves and the open source community is forced to reverse-engineer them.  In short, stop bellyaching because your machine is freezing.  It's probably your machine's fault and not "Linux!"

---

### Post by BRODEL on 2007-11-12
I found this post while googling for the problem wondering if it was only my machine with the issue. It's happened to me twice now, the first time I thought it was just a fluke. 

Anyone have any suggestions on things to try? This really sucks for me since I use the system as a vmware server and when it locks up all of my VMs just die.. :(

---

### Post by FreeMinded on 2007-11-13
Dear all,

My flatmate justed installed ubuntu 7.10 upon my recommandation. Now he is hawing the same problem as discribed in this post.
Interesting is the that no startup splash appears and the booting takes for ever.
It's a IBM Thinkpad with an ATI Mobility 7500.

Any help is appreciated! Thanks.
FM

---

### Post by LegoAddict on 2007-11-14
I tried both of those solutions given above.  Neither helps, and for some reason ctrl-alt-<- doesn't work anymore...

This problem is really bothering me.  It basically makes Ubuntu unusable.

---

### Post by Pbethe on 2007-11-20
> **cmost said:**
> T  If you're using Ubuntu and it's freezing for you and you have verified there is no problem with your hardware (i.e., RAM, hard disk, cooling, graphics card, etc.) then switch distributions.  While Ubuntu aims to work well on the average hardware, it can't possibly work flawlessly on every single system.  Especially since hardware vendors fail to supply drivers themselves and the open source community is forced to reverse-engineer them.  In short, stop bellyaching because your machine is freezing.  It's probably your machine's fault and not "Linux!"

Maybe my old machine is just not up to running Ubuntu.  I tried Xubuntu 7.10 because it is said to be light weight, but that freezes up faster than the others.  Is there a distribution that is ultralightweight?  

I have managed to start a process monitor before things grind to a halt.  It shows that I am not close to 100% during the freezes.  The monitor will even keep going and show a little blip when I move the mouse.

If you or anyone else wants to look at some log entries that I captured, I will attach what I have.

Thanks,
Paul

---

### Post by gsiliceo on 2007-11-20
Damn small linux is the smallest usable i know.

---

### Post by ansky on 2007-11-29
I am also experiencing this freezing problem on my Thinkpad T60.  Mouse works but the keyboard has no effect, including restarting X or switching to a console.  The only option is a hard reboot.   Any suggestions for diagnosing this problem?  Some logs to look at?  Something to run in the background to capture when it occurs?  Although I have not found any pattern it happens regularly enough (every 1-2 days) that it wouldn't be hard to capture it if I knew what to look for.  Thanks.

---

### Post by PmDematagoda on 2007-11-29
For all the people who experience freezes on Ubuntu and want to know a cleaner way of rebooting instead of a cold reboot, I recommend you to look [here]("http://ubuntuforums.org/showthread.php?t=617349").

---

### Post by ppaulojr on 2007-11-30
I'm also having this kind of locks.

It happens randomly when I start an apt-get or a download.

My system is

AMD 64 X2 5200+
Asus M2N-X
SATA HD 250 GB
GeForce 8500 GT

It's getting unberable.

Any hints.

---

### Post by nymlord on 2008-02-16
I was having this problem, still do.. BUT what decreased the freezing a lot was uninstalling emerald, im running ubuntu 7.10 with compiz fusion, try not to put too many special effects as well. emerald themes seem to lag your computer a **** load, so i would recommend not using it at all and try and see if that helps.

---

### Post by Chappy7777 on 2008-02-20
> **FuturePilot said:**
> Try disabling powernowd. System>Administration>Services.
Uncheck CPU Frequency Manager (powernowd)
Reboot and see if that stops it.
========================
I am running 7.04 and for the 1st time ever the system froze completely. No mouse, keyboard,
force quit, nothing. 

I have tried what you suggested above (unchecking powernowd). I don't know if it is the right thing to do or not, since, as I said, my system freeze is a first after many months of use. My CPU and Ram were not maxed out. I was playing Solitaire and listening to steaming audio via Firefox's flashplugin. I do this often, so the freeze was a total shock.

I was under the impression that Linux doesn't freeze. Sigh. Like finding out there's no Santa.

Anyhow, do you think I should leave the powernowd unchecked? 

I read the note about pressing ctrl+alt+bksp, but that cannot be done in the system is frozen,  correct?

---

### Post by photismos on 2008-02-22
I'm very new to Linux, but I was having very similar errors....random freezing (even restarts at times) but usually still able to use my mouse, although to no avail since nothing was selectable, and of course the keyboard was completely useless (frozen)...nothing worked. It was happening intermittently, wondered if it was Firefox or my movie player or my NVIDIA driver something I was doing...NOT SO!  

I searched a few threads here and found that editing "/boot/grub/menu.lst" adding just two little words..."noapic nolapic" fixed it COMPLETELY. Since then I've had no freezes at all.

Here's where the those "words" went in the context of my menu.lst, if it helps you to know where to put it:

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-rt
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-rt root=UUID=56ef75eb-5ce9-4863-a4ee-2d4d2a167847 ro noapic nolapic quiet splash
initrd /boot/initrd.img-2.6.22-14-rt
quiet

...AND that's it. you put it in that "kernel" line and restart. Hope it helps. If it does, would be nice if you confirmed that for others... =) That's what I'm doing...trying to find the original thread(s) I found this solution in to confirm it works! =D ...well, again...hope it helps!

---

### Post by kaginken on 2008-02-22
Almost all of my laptops freeze after installing 7.10.  Reason is, all of these laptops don't have very good graphics cards, and cannot handle the compiz eyecandy that was enabled  by defaullt.

Easy solution here is to turn off compiz.

System --> Preferences --> Appearance --> Visual Effects tab --> Check 'None'.

Works like a charm.  :guitar:

Hope that helps!!

---

### Post by MPH on 2008-03-29
I recently moved my 7.10 Ubuntu hard drives from a 2002 PC to 2000 PC with a similar CPU and more RAM.  (I originally intended to use Ubuntu just to create a home file and print server.  Since I couldn't get enough help on the forum to learn the command line system, I installed the Ubuntu desktop.)  The 2002 PC was a budget model (college surplus) yet it never froze up.  The 2000 PC has a Diamond Stealth S540 video card and it freezes immediately when running the same Pipes screensaver used on the 2002 PC.  (Pipes was choosen because of its low CPU utilization on the 2002 PC.)   When the 2000 PC freezes, the mouse and keyboard are totally unusable so trying Ctrl-Alt-Backspace does nothing.

> Almost all of my laptops freeze after installing 7.10. Reason is, all of these laptops don't have very good graphics cards, and cannot handle [COLOR="Red"]**the compiz eyecandy that was enabled by defaullt.**[/COLOR]

Easy solution here is to turn off compiz.

System --> Preferences --> Appearance --> Visual Effects tab --> Check 'None'


When I checked the Visual Effects tab of my 2000 PC, "None" was already selected.  Apparently, the Ubuntu hardware installation/upgrade process must grade the video card's ability to run compiz.  Even though my current card must have no ability for significant visual effects (so _apparently_ the compiz feature turned off), the PC freezes immediately when trying to display a preview of Pipes.

Okay, I can live without a screensaver on a PC that's mostly used as a server so I'm not using a screensaver any more.   However, I do enjoy trying out some of the desktop apps so I wonder if anyone who had the screensaver freeze problem found any other software that would freeze their PC...

---

### Post by gsiliceo on 2008-03-31
I'd just like to point out that is a myth that screensavers increase the life of your screen, turning them off is way better for them and energy usage.

---

### Post by MPH on 2008-04-01
True... and most screensavers are so compute-intensive that the PC consumes more power when running them than when idling.

However, since I still have a nice CRT, I hate to hear the electrostatic field collapsing as it enters power-saver mode just before I was about to use the PC again.  Thus, I like to use a simple screensaver as a "2-minute warning" for the impending CRT powerdown.

---

