---
title: "MC (Midnight commander) - Segmentation fault (core dumped)"
date: 2007-01-18
forum: General Help
---

### Post by Nikola Kasabov on 2007-01-18
Midnight commander crashes with an error - Segmentation fault (core dumped). This happens when I try to copy/move file or directory (press F5 or F6) and one of the panels is changed to "Info". If both panels are "Listing" then there are no problems.

Does someone solved such or a similar problem with MC?

---

### Post by dominicedmonds on 2008-02-27
Me too, running Debian Etch on a Linksys NSLU2 and on Gutsy 7.10 on a Dell Latitude D810.

Any ideas so far? Dominic

---

### Post by lam2988 on 2008-03-05
hi, i too am having a proble with this error. after a upgrade i can not open firefox and i type firefox -safe- mode. and i get the segmentation fault ( core dumped) i do not know what to try anyone help.:confused:

---

### Post by abyssius on 2008-03-09
I've reviewed several threads that describe Firefox crashing problems with  segmentation error (core dumped). I'm hesitant to add yet another. However, I've not been able to find a post that actually fixes the problem described below.

First, some reference info:
The kernel I'm having problems with: Linux 2.6.22-14-rt #1 SMP PREEMPT RT Tue Feb 12 09:57:10 UTC 2008 i686 GNU/Linux. Note: I installed this kernel over the original generic version so I could use Rosegarden.

As for FireFox, other than adding bookmarks, I installed the flash9 and realplayer10gold plug-ins and Java6 runtime.

The problem is that Firefox seems to crash randomly during normal usage. To be more specific, the Firefox screen will completely vanish when clicking on a link or scrolling a page, etc. After a few occurences, I tried starting firefox via the terminal. When a crash occured, I'd check the console, and note the following message:
> Segmentation fault (core dumped).
or on one occasion:
> Illegal instruction (core dumped)
After reviewing some posts describing similar problems, I tried the following recommendations:

Solution 1 Attempt:
```
killall firefox-bin
```
then restart firefox - no effect, still crashes randomly with segmentation fault (core dumped)

Solution 2 Attempt:
```
mv .mozilla .mozilla.old
```
then restart firefox - no effect, still crashes randomly with segmentation fault (core dumped)

Solution 3 Attempt:
```
firefox -ProfileManager
```
Wouldn't even run. Immediate segmentation fault (core dumped)

Finally, firefox locked up the mouse and keyboard. I was forced to invoke a hard reset. However, my system would not reboot properly. It would  continuously scroll (error messages??) so fast that they couldn't be read.  Several hard resets later, fsck was automatically triggered. After this process, the system was able to boot to a command prompt. I immediately ran:

```
apt-get --purge remove firefox

apt-get install firefox
```

The following message came up during the re-install process:

> Warning: Something created compreg.dat!
Your system was affected by this bug:
[http://launchpad.net/bugs/3079/](http://launchpad.net/bugs/3079/)
Compreg.dat has now been removed again, which should fix the problems.

Wow! great. Upon reboot, the system booted up to GUI normally. I ran firefox. It seemed to be working. I ran ProfileManager - no problems. I went to the launchpad bug URL listed above. From my newbie perspective, this page didn't seem to provide any relevant information. Anyway, I assumed that with the freshly re-installed FireFox, and that reassuring message, Firefox must now be fixed. Wrong. Firefox still crashes  seemingly at random with the now familiar: Segmentation fault (core dumped).

It seems like Firefox simply won't work reliably with this computer. It's a shame, since I've used FireFox on my Windows computer for ages without a single problem. Anyway, before I have to settle for Opera (which I am not fond of, but works flawlessly), does anyone have any other troubleshooting ideas?

---

### Post by kerry_s on 2008-03-09
i think you should have started your own thread, this has nothing to do with MC as is the title of the thread.

---

