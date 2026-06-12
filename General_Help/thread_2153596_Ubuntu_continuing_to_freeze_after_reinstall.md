---
title: "Ubuntu continuing to freeze after reinstall"
date: 2013-06-11
forum: General Help
---

### Post by maraym on 2013-06-11
Hello - 

I posted a few weeks ago [http://ubuntuforums.org/showthread.php?t=2145127](http://ubuntuforums.org/showthread.php?t=2145127) about repeated freezing issues that started occurring earlier this year.

This afternoon, I reinstalled Ubuntu 12.04, following these instructions [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) . FWIW, my original /etc/fstab is posted below.  I retained the same partitions and mount points, and I did not reformat any of the partitions.

The system froze again, twice, after installation.

So I switched to a command prompt and did an apt-get update and an apt-get upgrade (240 packages).  The upgrade hung with what I can only describe as a slow, repeating rewrite of the screen contents.  The only messages I caught that stuck out were a bunch of "soft lockup CPU#0 stuck for 22s" messages (same messages for CPU#1 also). I did an autoremove/autoclean/update/upgrade sequence as described in [http://askubuntu.com/questions/173648/recover-the-package-manager-after-crash-during-update](http://askubuntu.com/questions/173648/recover-the-package-manager-after-crash-during-update)
 

Any ideas why this is happening, or what to try next?  Is there some configuration file somewhere on my /home drive that might be causing this?


PS - Another issue - If I switch to a command prompt (ctrl-alt-f1), I can't  get back to the desktop (ctrl-alt-f7).  The screen flickers repeatedly, and I never get to the desktop.  This occurred while I was composing this post (yay auto-save!), and I had to hard boot.


```
mike@mike-g6-2022:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=0545ff8d-7c4f-493b-ac46-ae037750a42f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=4a225e58-66cc-4b4f-85ce-3062520bec2d /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=44dcb390-14fd-4ba1-8a2c-9a3c3f3dcea2 none            swap    sw              0       0

```

---

### Post by ahallubuntu on 2013-06-11
~

---

### Post by ahallubuntu on 2013-06-11
~

---

### Post by maraym on 2013-06-11
allahubuntu - 

Thanks very much for your replies!

I'm not at all sure the CPU isn't overheating... the fan vents aren't immaculate, but they're not blocked.

I do want to note two things, though:

1) it's a dual boot, and I have no problem when I run windows 7
2) I ran 12.04 without ever freezing even once, for 5 months (until mid-March) 

As noted in an update to my original post, I ran a complete memory test the other day and it found no errors.  (I should note that I first attempted to run the complete memory test when I first got the memory upgrade back in March.  The laptop shut down prior to completing the test.  The other day I ran a fan on the laptop to ensure that the test ran to completion)

As to the version that I used for the re-install:

```
-rw-rw-r-- 1 mike mike  728760320 May 24 12:18 ubuntu-12.04.2-desktop-amd64.iso
```

I burned the DVD this morning, and ran the "test for defects" check prior to reinstallation.

Thanks again for your replies

---

### Post by ahallubuntu on 2013-06-11
~

---

### Post by maraym on 2013-06-11
> **ahallubuntu said:**
> My guess would be the CPU is indeed overheating, if you can't finish the memtest without a fan blowing on it.  That doesn't mean your fan/CPU heat sink is dirty (especially as you say you have no issues in Windows).  It could mean the kernel isn't installing the right driver for the CPU to go into power-savings mode.  Or the same for the graphics card.  More RAM also means more heat - could mean it's running hotter now than before you upgraded the RAM.

I assume you are aware of what the fan sounds like when the laptop is  getting hot?  The fan should spin faster (louder) when it's running  hotter?  Do you notice the fan faster/louder in Ubuntu just before it  shuts down?

From my original post (I know, it was really long):

Other symptoms

[LIST]
[*]running hot 
[*]fan ran more often, and at higher intensity 
[*]high CPU usage from Xorg (often 40-70% of a CPU (in top)) 
[/LIST]

Note that an upgrade on 5/13/2013 resulted in:

Other symptoms' much improved

[LIST]
[*]running cooler 
[*]fan runs less often, and at much lower inensity 
[*]low CPU usage from Xorg (generally < 10%) 
[/LIST]

The Xorg CPU usage remained (to this day) at < 10%, but I may have spoken too soon on frequency and intensity of fan usage


How can I determine if "kernel isn't installing the right driver for the CPU to go into power-savings mode"? (See hardware details below)

> **ahallubuntu said:**
> About the memory test: were you using the Linux-based Memtest or the Windows 7 (or HP) memory test?

I ran the GRUB menu memory test

> **ahallubuntu said:**
>  Normally I don't recommend the short-term support editions of Ubuntu (like 13.04, supported for only nine months), but in cases like this I suggest exploring them to see if the newer kernel helps.

I'll look into this.  I'm also going to try digging up the original install CD and try re-installing that.

> **ahallubuntu said:**
>  You could also check to see if you have the right video card driver (sorry, didn't read your whole other thread, maybe you tried that).  There may also be ways to monitor the CPU power state for your specific CPU.

I wouldn't be surprised that I might not "have the right video card driver".  Could you give me a little advice on that?  (again, see hardware details below) 

After the reinstall there was a notification up next to my email/network/sound... icons indicating that there was something else available to be installed (proprietary drivers?), but I don't see that any longer.  I should also note that I had a real hard time with those when I first installed back in October, and ended up having to uninstall them.

btw - the only errors in /var/log/Xorg.0.log are:

```
[    20.630] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    20.631] (EE) Failed to load module "fglrx" (module does not exist, 0)

```


> **ahallubuntu said:**
>  Also, I'd check the HP website for BIOS updates for your laptop and if there's a newer BIOS available, install it (in Windows).  Sometimes such updates will fix issues as you describe.

Ok... I'll look into that

Hardware:

HP Pavilion g6-2123us Notebook PC
3.0GHz/2.6GHz AMD Dual-Core A6-4400M Accelerated Processor
AMD Radeon HD 7520G

More hw info [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03331680&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=5273777](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03331680&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=5273777)

---

### Post by ahallubuntu on 2013-06-11
~

---

### Post by maraym on 2013-06-11
> **ahallubuntu said:**
> I'd look here for more info about installing a proprietary driver for your video card:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

You wouldn't be the first person to have issues with this graphics card or the proprietary driver.  Here's one example (not exactly the same issues):

[http://ubuntuforums.org/showthread.php?t=2105778](http://ubuntuforums.org/showthread.php?t=2105778)

Note that the last poster mentioned that 13.04 worked better.  Given that, I'd probably try it.  I also read that the 13.04 kernel may wind up getting added to 12.04 LTS (12.04.3 ?) at some point as a standard, so you may be able to revert back to 12.04.3 at some point if 13.04 works (13.04 supported only until January).

Check out the attached screenshot...


I've got to head to a Python user group meeting.  I'll check back later.

Thanks again!

---

### Post by ahallubuntu on 2013-06-11
~

---

### Post by maraym on 2013-06-12
The last time I tried the experimental drivers, I couldn't get the Unity desktop.  All I got was a black screen.  And I've never had good feelings about the reversion process.  But that was back in October, and this problem didn't arise for another 5 months

btw - I just realized that I misread/misspelled your name.  Sorry!

---

