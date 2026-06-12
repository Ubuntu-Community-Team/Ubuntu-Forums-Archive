---
title: "Possibly a graphics issue..."
date: 2008-02-07
forum: General Help
---

### Post by Silent Warrior on 2008-02-07
... but then again, maybe not. I don't know what to make of this at all.

First of all, the system this is occurring on:
Pentium 4 2GHz
512 Mb RDRAM
ATI Radeon 9600
Creative SBLive! Platinum 5.1
Kubuntu 7.10 (KDE3 at its base with KDE4 installed, but not in use. Enlightenment is also installed, along with a few Gnome-libraries.)

Lately I have had a real struggle with graphics-drivers... Installing ATI's drivers have never really worked as I would've hoped, and I recently discovered I've been using the vesa-driver for, well, ever. I'd hoped to change that, and after monkeying around with xorg.conf and god knows what else, I've resigned myself to the conviction that FGLRX is a whole lot more trouble than it's worth. Although it seemed like I got actual display out of it. Once. And then I could ABSOLUTELY not reach kdm.
As in, turn on power, wait for everything that needs loading to load before logging in, and end up staring at a completely unresponsive command-line blinking marker and little else. No progression from there. So, to try the 'ati'-driver. I believe it worked (I don't always bother to check), and now it doesn't. Same symptom.
Bugger! Fallback to vesa, and it was quite the same thing - worked for a while, and now it doesn't.

Recent package-activity includes a KDE4-update (although it isn't used because vesa is too slow), a minor kernel update (I think... linux-kernel-headers and such were updated) and maybe a few libraries (i.e. less than 5).

What do I do now? Go Gentoo? :p

---

### Post by kesman on 2008-02-07
Have you tried installing ati drivers with envy? Worked for me.

---

### Post by Rocket2DMn on 2008-02-07
It should work with the ati driver just fine, you can check this link - [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
It tells you how to remove the fglrx driver and properly setup the ATI driver.  You might need to reconfigure X if you've fiddled with xorg.conf manually
```
sudo dpkg-reconfigure xserver-xorg
```
That will ask a bunch of questions about your hardware, do your best to answer.  Use TAB to move and SPACEBAR to select your monitor's max resolution and everything else.  Select the "ati" driver when prompted.  Then restart X with CTRL+ALT+BACKSPACE

---

### Post by Silent Warrior on 2008-02-08
Well, I think I managed to uninstall FGLRX, but that's about all the success I had... I can launch the desktop just fine in Recovery mode (GRUB-menu), but kdm just won't start normally.

It turns out said uninstallation wasn't quite clean. It left a directory still standing in /usr/lib, containing a file called libGL.so.1.xlibmesa. What do we say to that?

---

### Post by Rocket2DMn on 2008-02-08
So did you follow the directions at [https://help.ubuntu.com/community/RadeonDriver#head-229f59879c2a2b6c6635d1e189706d97f836b879](https://help.ubuntu.com/community/RadeonDriver#head-229f59879c2a2b6c6635d1e189706d97f836b879) then reconfigure X like I showed above?  If kdm won't start, do CTRL+ALT+F1 to get to a terminal, stop kdm, reconfigure, and restart kdm.  Make sure you are in normal mode so you have networking.
```
sudo apt-get remove --purge xorg-driver-fglrx
glxinfo |grep vendor
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

sudo /etc/init.d/kdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/kdm start
```

Select the "ati" driver during reconfiguration.

---

### Post by Silent Warrior on 2008-02-09
I followed that guide as closely as possible. As I couldn't get into normal Kubuntu, I didn't have networking and couldn't download the packages to reinstall and had to get them off Debian's online package-pool. I tell you, mounting the USB-memory was a struggle to behold... Well, after manually starting kdm and such.
Nothing happens when I hit CTRL+ALT+F1... After a normal boot. CTRL+ALT+DEL works, of course, but I don't see that helping much.

Typing [sudo /etc/init.d/kdm start] in Recovery mode gets me a message that kdm isn't the default display-manager. Could that be a clue? [Not really - changed default-display-manager to use kdm instead of kdm-kde4.]
Anyway, X.org is yet again reconfigured... I can probably do this with my eyes closed soon. Rebooting...

Heh! Fancy that! It seems to be working now. Cool beans!

---

### Post by Silent Warrior on 2008-02-09
Uh... Belay that... Most likely due to previous tinkering, something's REALLY not right with my /usr/lib/libGL.so.1. When I try to update, or fix the buggered dependencies, I get the message that there's no such file or directory. libgl1-mesa-glx is the affected package, which affects a few neighbouring ones, Adept shows a few as BROKEN (upgradeable). Force-installing the package (mesa-glx) doesn't work.
I've also tried to download the Mesa project's source-code and compiling it, but I haven't managed that yet - it seems like I'm missing some files - headers, libraries - and Adept/Synaptic are completely incapacitated until the dependencies are improved.

Am I screwed NOW?

Still, this has got to serve as a testament to the robust design of Linux - no Windows EVER would let me onto the desktop if key components were in this state!

---

### Post by Rocket2DMn on 2008-02-09
Can you please run
```
sudo apt-get update
sudo apt-get upgrade
```
If anything out of the ordinary shows up, please post it.
You can also try
```
sudo apt-get build-dep *packagename*
```

---

### Post by Silent Warrior on 2008-02-10
Running apt-get update/upgrade makes this happen:
```
Bygger beroendeträd
Läser tillståndsinformation... Färdig
Du kan möjligen rätta till dessa genom att köra "apt-get -f install".
Följande paket har beroenden som inte kan tillfredsställas:
  libgl1-mesa-dev: Beroende av: libgl1-mesa-glx (>= 7.0.1) men 6.5.1-0.6 är installerat
  libgl1-mesa-dri: Beroende av: libgl1-mesa-glx (= 7.0.1-1ubuntu3) men 6.5.1-0.6 är installerat
E: Otillfredsställda beroenden. Prova med -f.
```
(If you didn't know, this is Swedish. :) )
It translates to
```

Building dependency-tree
Reading state-information... Done
You can possibly correct these by running "apt-get -f install".
The following packages have unsatisfiable dependencies:
  libgl1-mesa-dev: Depending on: libgl1-mesa-glx (>= 7.0.1) but 6.5.1-0.6 is installed
  libgl1-mesa-dri: Depending on: libgl1-mesa-glx (= 7.0.1-1ubuntu3) but 6.5.1-0.6 is installed
E: Unmet dependencies. Try -f.
```

Running build-dep on either package is unsuccessful.

---

### Post by Rocket2DMn on 2008-02-10
Let's try to run a dpkg reconfigure
```
sudo dpkg --configure -a
```

Now try reinstalling that dependency package
```
sudo apt-get install --reinstall libgl1-mesa-glx
```
Version 7.0.1 is available in the repositories - [http://packages.ubuntu.com/gutsy/libs/libgl1-mesa-glx](http://packages.ubuntu.com/gutsy/libs/libgl1-mesa-glx)

If it doesn't let you reinstall, uninstall the dependency package, then install fresh
```
sudo apt-get remove libgl1-mesa-glx --purge
sudo apt-get clean
sudo apt-get update
sudo apt-get install libgl1-mesa-glx
```

---

### Post by Silent Warrior on 2008-02-10
Dependency-problems prevents the dpkg --configure-line, and reinstalling runs into that problem creating a symbolic link.

There's an Ubuntu package-pool online too? If I'd only known that before... And I'm not allowed to uninstall libgl1-mesa-glx - lots (and I mean LOTS) of other packages depends on it (imagine that) and to sum it all up, the output says 'Nah!' But, I'll try some other ways to get this uninstalled.

---

### Post by Rocket2DMn on 2008-02-10
OK, well if it says don't do it, then don't do it.
Can you please post the output of the dpkg command so I can see it (in English please :))?

---

### Post by Silent Warrior on 2008-02-11
Never mind, I reinstalled Kubuntu from CD. Loads easier... And certifiably works.

But, to answer your question: It seemed like the main idea was that libgl1-mesa-glx was broken somewhere along the way, causing depdendency-havoc, and since no remedial package acknowledged the existence of libGL.so.1 (or whatever it's called exactly) or had any desire to put its own file/symlink there instead, it seemed rather... dead-end-ish. It was VERY explicit about not finding libGL.so.1.

---

### Post by Silent Warrior on 2008-02-14
GAAH! What in tarnation? OK, this might not be a serious problem at all (though I have my doubts), but it sort of recurred just now. I had just installed Compiz (and it WORKS! And how fast it is!) and on the next boot-up I had this uncooperative KDM again. And since I haven't let FGLRX anywhere near my computer this time around, libGL and all its associates are squeaky-clean.
This time, I left it well alone for a while as I had something else to do, and when I came back, I'm greeted by sparkly little KDM demanding my password like nothing every happened. Uh...

WHAT - IN - THE - NINE - HELLS - IS - MY - COMPUTER - DOING??

---

### Post by Rocket2DMn on 2008-02-14
Recent updates have fiddled with some people's video cards, esp. those using proprietary nvidia drivers, but that doesn't seem to be your case.  Is everything still working?

---

### Post by Silent Warrior on 2008-02-15
It booted in what passes for normal circumstances here... It appears so. It takes 15-30 seconds before KDM loads after all the drivers and drives have been checked and mounted and whatnot - which I consider ABnormal - but otherwise all's well.

---

