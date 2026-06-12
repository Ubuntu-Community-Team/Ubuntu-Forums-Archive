---
title: "Ubuntu 13.10 unity crash"
date: 2014-02-17
forum: General Help
---

### Post by al3arbe1 on 2014-02-17
Hello,

I use Ubuntu 13.10

is I use Ubuntu 10 hours or after ..

This Ubuntu ! from 12.04 to 13.10 after 10 hours work
[http://imageshack.com/a/img833/228/0nab.jpg](http://imageshack.com/a/img833/228/0nab.jpg)
[http://imageshack.com/a/img89/8955/81jp.jpg](http://imageshack.com/a/img89/8955/81jp.jpg)
[http://imageshack.com/a/img845/8214/wv6m.jpg](http://imageshack.com/a/img845/8214/wv6m.jpg)

plase help me

I require for all login ubuntu change again at change keyboard to alt + shift

Sorry .. I Weak in English

---

### Post by al3arbe1 on 2014-02-18
Do you need additional information?

---

### Post by varunendra on 2014-02-18
Welcome to the forums al3arbe1 !

Probably the first useful information you can provide is your native language. So what is your Native Language? Maybe we can find you a help source which you can be more comfortable with.

And since it seems to be a graphics issue from the screenshots, maybe a look at your graphics card and driver may help with the actual problem.

If you can boot into a usable graphics mode with a Live CD/USB, pleas post back the output of the following command to give us that info -
```
sudo lshw -C display
```

And with the installed system, try 'nomodeset' option as explained in the first post here : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Feel free to ask if you have problem understanding the post or any of the suggestions.

---

### Post by al3arbe1 on 2014-02-18
The problem sometimes
I try this from ubuntu 13.10 - not problem now .. after hours problem
```

sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: GT218 [GeForce 210]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fa000000-faffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fb000000-fb07ffff
```

Ubuntu Linux on full Hard Disk

---

### Post by varunendra on 2014-02-18
So it occurs after working fine for a few hours?

If so, I would suspect the memory first.

If you get the Grub menu at boot time, where you can select to boot Ubuntu, Ubuntu recovery mode, Run memtest+ etc, select memtest+
If you don't get that menu by default, tap 'Shift' key as soon as the system starts booting (keep tapping the key until you get the menu). On some systems, it can be 'Esc' key instead of 'Shift'.

Run memtest+ at least 6-8 hours (better start it in the night or when you can leave it running that long), and see if it reports any "Fail" or hangs while running it. If not, the memory can be considered to be good. Otherwise it may be a memory leakage problem - means bad RAM.

It can also be a loose card (including RAM) or a loose cable, or another component that gets overheat after a few minutes/hours of working. But memory is the prime suspect in such cases where system boots fine, then suddenly crashes with weird graphics on the screen.

---

### Post by al3arbe1 on 2014-02-18
> **varunendra said:**
> So it occurs after working fine for a few hours?

Yes


> **varunendra said:**
> 
If so, I would suspect the memory first.

If you get the Grub menu at boot time, where you can select to boot Ubuntu, Ubuntu recovery mode, Run memtest+ etc, select memtest+
If you don't get that menu by default, tap 'Shift' key as soon as the system starts booting (keep tapping the key until you get the menu). On some systems, it can be 'Esc' key instead of 'Shift'.

Run memtest+ at least 6-8 hours (better start it in the night or when you can leave it running that long), and see if it reports any "Fail" or hangs while running it. If not, the memory can be considered to be good. Otherwise it may be a memory leakage problem - means bad RAM.

no errors, pass Esc to exit ...

> **varunendra said:**
> 
It can also be a loose card (including RAM) or a loose cable, or another component that gets overheat after a few minutes/hours of working. But memory is the prime suspect in such cases where system boots fine, then suddenly crashes with weird graphics on the screen.

How do I know ?

This Images For error and memtest+
[http://www.4shared.com/file/xBUmnaJace/UbuntuErrorstar.html](http://www.4shared.com/file/xBUmnaJace/UbuntuErrorstar.html)

---

### Post by varunendra on 2014-02-18
Leave memtest running continuously for at least 6-8 hours (recommended duration is 24 hours by the way, but 6 to 8 hours should be enough to prove it *reasonably* stable). It should Pass several passes in this duration. Successfully passing just 2-3 passes means nothing.

---

### Post by al3arbe1 on 2014-02-21
duration 38 hours (100 pass) is ok no errors

[http://imageshack.com/a/img196/959/06m6.jpg](http://imageshack.com/a/img196/959/06m6.jpg)
[http://imageshack.com/a/img834/9269/krmx.jpg](http://imageshack.com/a/img834/9269/krmx.jpg)

---

### Post by varunendra on 2014-02-21
I think I am getting out of ideas, especially since I have rarely used dedicated graphics so far (I'm always happy with the onboard graphics), and have never 'Upgraded' Ubuntu (I always prefer a fresh install).

Please give us a complete detail of your hardware and drivers in use. To do so, run the following commands in a terminal -
```
sudo lshw -numeric -sanitize > Desktop/lshw.txt
lsmod > Desktop/lsmod.txt
cp /var/log/syslog Desktop/syslog.txt
cp /var/log/Xorg.0.log Desktop/xorg.txt
```
These will create certain "..**.txt**" files on your desktop. Upload their contents on [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) and post back the pastebin URL that you get after submitting it.

The graphics experts would probably also ask you to show them your Nvidia graphics related logs, but I don't know their names so can't say exactly which ones. Probably take a look in your /var/log directory and if you see any Nvidia graphics related log file, include its contents too in the above pastebin URL.

**PS:**
If anyone reading this thread have any ideas about how to find the problem or what to try, please join us. Thanks!

---

### Post by al3arbe1 on 2014-02-22
This all files

lshw.txt
[http://pastebin.ubuntu.com/6974521](http://pastebin.ubuntu.com/6974521)

xorg.txt
[http://pastebin.ubuntu.com/6974522](http://pastebin.ubuntu.com/6974522)

syslog.txt
[http://pastebin.ubuntu.com/6974524](http://pastebin.ubuntu.com/6974524)

lsmod.txt
[http://pastebin.ubuntu.com/6974527](http://pastebin.ubuntu.com/6974527)

---

### Post by varunendra on 2014-02-22
Nope, I couldn't get any clues in them (even if there were, I couldn't catch them). Maybe also upload the Xorg logs of the previous session (when the session crashes and you have to reboot). These would be -
```
cp /var/log/Xorg.0.log.old Desktop/xorg-old.txt
cp /var/log/Xorg.1.log Desktop/xorg1.txt
cp /var/log/Xorg.1.log.old Desktop/xorg1-old.txt
```
And in the meanwhile, please try the "nomodeset" option to load the system in low graphics mode : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

In low graphics mode, the graphics driver is not in use, so you will get no hardware graphics acceleration and the system may be slow, laggy while working. But if the problem is caused due to graphics driver, then it shouldn't occur in this mode.

So for now, please apply the "nomodeset" option temporarily or permanently, and see if it makes the system stable (even if slow, but stable). If yes, then the culprit is the graphics driver and you may need to either change/update it, or do some tweaks to make it stable.

This is just my guess and honestly I have no idea what is going on. The logs I asked above just contain some more information about the X-session. So may be we can get some clues there.

---

### Post by al3arbe1 on 2014-02-22
This
Xorg.0.log.old
[http://pastebin.ubuntu.com/6975737/](http://pastebin.ubuntu.com/6975737/)

Xorg.1.log and Xorg.1.log.old is empty!

This error not in all time

I require for repair in after time

---

