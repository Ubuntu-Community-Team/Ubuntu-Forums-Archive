---
title: "After updating FGLRX driver, can't log into desktop (Ubuntu 14.04)"
date: 2015-04-15
forum: General Help
---

### Post by azzach19 on 2015-04-15
Hello, I just ran some weekly updates for my computer which is running Ubuntu 14.04. I noticed that in the updates I updated the fglrx drivers, and there were some errors popping up through the update process. I managed my way through the errors using ```
[COLOR=#111111][FONT=Consolas]sudo apt-get update-f[/FONT][/COLOR]
``` using the terminal. At one point I was prompted to hit "Y, N, I, O" in the terminal if I remember correctly to write over some config files (I hit Y for every option). and then I restarted my computer as requested. Now, when I get the the password screen before the desktop, I can't actually log into the desktop when I enter my password. It looks like its about to log me in and then it goes straight back to the password screen. No red text error pops up such as incorrect password. I don't believe that I'm using an incorrect password because guess session has the exact same result.

---

### Post by Bashing-om on 2015-04-15
azzach19; Hi ! Welcome to the forum .

Well, at the 1st I had suspected that a proprietary driver got broke in the update process ( ubuntu is not responsible for proprietary drivers. and how these drivers integrate with a changed system) .. but with login issues I suggest we look at authorization to   access your desktop.
At the log in screen key combo ctl+alt+F1 to gain a console.
Login here at this interface with your user name and password.

What results from terminal commands:
```

ls -al .Xauthority
ls -al .ICEauthority
echo $XAUTHORITY

```

[INDENT][INDENT]and that tale is told
[/INDENT][/INDENT]

---

### Post by azzach19 on 2015-04-15
Hello Bashing-om,

I tried the commands you listed, and here was the response for each.

```
ls -al .Xauthority
-rw-------- 1 usr usr 58 April 15 10:00

ls -al .ICEauthority
-rw-------- 1 usr usr 58 April 15 8:00

echo $XAUTHORITY
(no output)
```

Also, I tried to use startx from the terminal that I was in and I got this response which may be interesting:
```
Log file "/var/log/Xorg.1.log"
Using config file: "/etc/X11/xorg.conf"
Using system config directory "/usr/share/X11/xorg.conf.d"

Initializing... (removed full output for brevity)

Loading extension GLX
[KMS] drm report modsetting isn't supported
xinit: connection to X server lost
```

---

### Post by Bashing-om on 2015-04-15
azzach19; Well ..

Agreed, looks to be a broken graphics driver.
Can you boot to the desktop through grub's "recovery console " ?
At the bios boot screen, press and hold the right -shift- key -> grub menu  -> advance options -> recovery kernel.

If so, we can rebuild the proprietary graphics driver .

[INDENT][INDENT]it's buntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by azzach19 on 2015-04-15
> **Bashing-om said:**
> azzach19; Well ..

Agreed, looks to be a broken graphics driver.
Can you boot to the desktop through grub's "recovery console " ?
At the bios boot screen, press and hold the right -shift- key -> grub menu  -> advance options -> recovery kernel.

If so, we can rebuild the proprietary graphics driver .[INDENT][INDENT]it's buntu[INDENT][INDENT][INDENT]it is fixable
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]



I think I got to the Recovery Menu. I was at the grub boot screen and I went into advanced settings and loading one of the recovery mode kernels listed (I think it was Linux 3.13 something or other), and then I got to another menu. I didn't write down all the options but it said:
```
Recovery Menu (read-only)
resume
clean
dpkg
...
...
<OK>
```

I was going to try dpkg but I wasn't sure if that was right or what to do next.

---

### Post by Bashing-om on 2015-04-15
azzach19; Sorry;

My opologies for a failute in completeness.
All we want to know presently is that you can boot to the GUI ....
choose the "resume" option ... for now.
Hopefully boot to the desktop but in this instance only will be in a read only mode.. which is ok for just checking.

[INDENT][INDENT]small steps still gets results.
[/INDENT][/INDENT]

---

### Post by azzach19 on 2015-04-15
No problem, I went into resume and it took me to the login screen (right after the little drum beat sound). I used my password and the same issue that I mentioned in the OP happened. It looked like I was logging in and then it brought back the login screen (no error messages or anything). Same result using guess session as well.

---

### Post by Bashing-om on 2015-04-15
azzach19; Hummm ...

That condition does not compute with my thought process.... 
OK, Let's boot to terminal - not console - and do some deeper look'n.
At the grub menu press the 'e' key for edit mode -> boot parameter screen;
arrow down to the line similar " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff " arrow across to "quiet splash" and replace these terms with the term 'text' - without the quotes;
key combo ctl+x to continue the boot process to TTY1.
Login here with user name and pass word:
what now results:
```

sudo lshw -C display

```My output for reference:
```

sysop@1404mini:~$ sudo lshw -C display
[sudo] password for sysop: 
  *-display:0             
       description: VGA compatible controller
       product: RV515 [Radeon X1300/X1550]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:16 memory:e0000000-efffffff memory:fd4f0000-fd4fffff iopt:4c00(size=256) memory:fd400000-fd41fff
<snip>

```
where of interest here is the description, product and configuration lines; as you have no access to the GUI to copy/paste, keep this as simple as possible. This will give the card info and if a driver is loaded .

[INDENT][INDENT]not so simple now
[/INDENT][/INDENT]

---

### Post by azzach19 on 2015-04-15
OK, here's my output:

       ```

description: VGA compatible controller
product: Cape Verde PRO [Radeon HD 7750 / R7 250E]
...
configuration: driver=fglrx_pci latency = 0

```

---

### Post by Bashing-om on 2015-04-15
azzach19; Hummm ...

I honestly do not know, system is stable as you can operate from the command line,
proprietary graphics driver is loaded;
authorizations are valid;
a quick search does not indicate any problems with that card on 'buntu.

Let's keep the focus as a graphics driver issue.
Post the contents of the Xorg log file:
from the TTY1 terminal install the pastebin tool:
```

sudo apt-get install pastebinit

```
and to post it:
```

cat /var/log/Xorg.0.log | pastebinit

```
which will give a URL back in terminal.
Post back that URL and let's see what we can make of the graphics situation.

By the way, what Desktop are you using ? unity ?

[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by azzach19 on 2015-04-15
I'm using the unity desktop GUI I believe (I never changed the default that ships with Ubuntu and I figure that's Unity). Also, I followed the commands you mentioned, and when I try ```
/var/log/Xorg.0.log | pastebinit 
```it says something about command /var/log/Xorg.0.log not found (I also had to use sudo to get permission).

Would it be possible to purge the FGLRX drivers and reinstall them? I had been using them fine before I ran today's update on them.

edit: and I don't think I had a /var/log/Xorg.0.log file at first, but I created it when I typed the commands. However, I did have a /var/log/Xorg.0.log.old file if I remember correctly.

---

### Post by QIII on 2015-04-15
Yes, you can get rid of the fglrx driver by issuing

```
sudo apt-get purge fglrx fglrx-updates fglrx-amdcccle fglrx-amdcccle-updates
```

Please issue the command to remove all four packages or apt may try to replace one with the other.

When you are done, you need to get rid of (actually we'll rename it for now) xorg.conf

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

While Ubuntu doesn't use an xorg.conf by default, one is created when you install AMD or NVIDIA proprietary drivers.

If you still can't start, we may need to have you reinstall some bits and pieces of other open source packages.

---

### Post by Bashing-om on 2015-04-15
azzach19; My  bad:

correct the command to be:
```

cat /var/log/Xorg.0.log | pastebinit

```

Hi QIII - our resident FGLRX guru - pleased to see ya drop in here :) .

[INDENT][INDENT]back up is nice 
[/INDENT][/INDENT]

---

### Post by QIII on 2015-04-15
Guru?

Nah.  Just smoke, mirrors and sleight-of-hand, man!

And there is a distinct possibility that this is a Xauthority issue, but one thing at a time.

---

### Post by azzach19 on 2015-04-15
> **Bashing-om said:**
> azzach19; My  bad:

correct the command to be:
```

cat /var/log/Xorg.0.log | pastebinit

```[INDENT][INDENT]
[/INDENT]
[/INDENT]


Ah, thanks, OK I have made 3 separate pastes for the 3 different files I have that seem to be Xorg related in /var/log directory.
[Xorg.0.log]("http://paste.ubuntu.com/10830374/")
[Xorg.0.log.old]("http://paste.ubuntu.com/10830380/")
[Xorg.1.log]("http://paste.ubuntu.com/10830384/")

---

### Post by Bashing-om on 2015-04-15
azzach19; Wellll ...

@QIII, If the magic is so good it is indistinguishable from real -> what is the difference ? 
After all, it is the result that counts .

Xorg.0.log:
reading the log -> looking good, looking good ->
Uh oH !
> 
28.614] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-15.20.1013
28.617] (EE) Unable to initialize PCS database
28.617] (EE)   Missing PCS defaults file /etc/ati/amdpcsdb.default
28.617] (II) [KMS] drm report modesetting isn't supported.
28.617] (EE) open /dev/dri/card0: No such file or directory
28.617] (**) FBDEV(2): claimed PCI slot 1@0:0:0
28.617] (II) FBDEV(2): using default device
28.617] (II) UnloadModule: "fglrx"
[    28.617] (II) Unloading fglrx
[    28.617] (II) UnloadSubModule: "fglrxdrm"

bk

28.617] (II) Unloading vesa


looks to me that the system is very unhappy with the proprietary driver, tried to load 'vesa' and could not .. and we wind up with no graphics driver loaded ??

Think at this point we do as QIII advises and purge FGLRX ... see if we come up then on the open source driver ... if so install the proprietary driver once more if still required - recently the open source drivers have come a long long way in performance.
And open source will not break in updates.

[INDENT][INDENT]I thought I was wrong once before -once upon a time - 
[INDENT][INDENT][INDENT][INDENT]it could happen again
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by azzach19 on 2015-04-15
OK, I'll try that Bashing-om, thanks for the help. Do I need to install anything after purging the fglrx drivers?

---

### Post by Bashing-om on 2015-04-15
azzach19; Hey;

No, I do not anticipate that you will 'need' to install anything ,,,,, but it is possible.
We cross that bridge if required. If needed we can  (RE-)install the open source driver.
Let's see how you like the open source driver, then take additional action as required.

[INDENT][INDENT][INDENT]that is what I think
[/INDENT][/INDENT][/INDENT]

---

### Post by azzach19 on 2015-04-15
Purging FGLRX drivers did the trick and I'm back on my Ubuntu desktop which is great. I'm going to try using the fglrx drivers again in the future because I need a more modern version of OpenGL (4.3) but I'm not necessarily in a hurry for that right now. Thanks for all the help.

---

### Post by Bashing-om on 2015-04-15
azzach19; Good deal !

Check that you are up presently on the open source driver "radeon"
```

sudo lshw -C display

``` that 'radeon' is in the configuration: line.

Then next step up for drivers available is the "Additional Drivers" utility .. Here also the driver will not break in the update process.

[INDENT][INDENT][INDENT]Up Up and away
[/INDENT][/INDENT][/INDENT]

---

### Post by azzach19 on 2015-04-16
> **Bashing-om said:**
> azzach19; Good deal !

Check that you are up presently on the open source driver "radeon"

that 'radeon' is in the configuration: line.

Then next step up for drivers available is the "Additional Drivers" utility .. Here also the driver will not break in the update process.[INDENT][INDENT][INDENT]Up Up and away
[/INDENT]
[/INDENT]
[/INDENT]


My configuration line says:

```
configuration: driver=fglrx_pci latency=0
```

And when I go to "Additional Drivers" all the fglrx options are not selectable and the only radio button selected says, "continue using a manually installed driver".

---

### Post by Bashing-om on 2015-04-16
azzach19; Welll ..

That output:
> 
configuration: driver=fglrx_pci latency=0

shows you are up and running with the proprietary graphics driver.

If all is good, then we are good,

[INDENT][INDENT]if it ain't broke, do not fix it
[/INDENT][/INDENT]

---

### Post by wbloos on 2016-03-30
Hi, I have the same problem, since an update of fglrx-updates came in on 2016-02-29
I've been trying to fix it since then, to no avail.
The symptoms:
* PC will boot normally, login screen shows, drum sound.
* When trying to login to a default (Unity) session, screen will flicker for a second and then return to the login screen without an error message
* Logging in to Metacity works, but not the other flashback option.

In Metacity i can switch between fglrx, fglrx-updates and nouveau without a problem (with the additional drivers tool).
When I change to nouveau, Unity will boot without problems.
I want to play games like Minecraft and Team fortress. This used to work with fglrx, but will not work with nouveau. Nor with fglrx in Metacity.
I have tried purging all fglrx packages like recommended above, but when i reinstall them, it's the same trouble. Adding nomodeset will not help.
I've tried the tips in [http://ubuntuforums.org/showthread.php?t=2244651](http://ubuntuforums.org/showthread.php?t=2244651) but aticonfig can't find /etc/ati/control (it isn't there).
```
me@me-desktop:~$ sudo aticonfig --initial
[sudo] password for me: 
Unable to open /etc/ati/control, please reinstall the driver.
aticonfig: No supported adapters detected
```

My system:
* Ubuntu 14.04
* GPU: Radeon R9 280X  
* Memory: 8GB DDR3
* Processor: Intel Core i5 4460
* Mainboard: ASRock B85M Pro4

lshw -C display
says:
```
       description: VGA compatible controller
       product: Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:16 memory:e0000000-efffffff memory:f0000000-f003ffff ioport:e000(size=256) memory:f0040000-f005ffff
```

In Xorg.0.log:
```
[    15.100] (II) AMD Proprietary Linux Driver Version Identifier:15.20.3
[    15.100] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-15.201.1151              
[    15.100] (II) AMD Proprietary Linux Driver Build Date: Sep  8 2015 15:06:35
[    15.100] (II) RADEON: Driver for ATI Radeon chipsets:
...(R9 280X not listed)...
[    15.103] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    15.103] (II) FBDEV: driver for framebuffer: fbdev
[    15.103] (II) VESA: driver for VESA chipsets: vesa
[    15.103] (++) using VT number 7

[    15.103] (WW) Falling back to old probe method for fglrx
[    15.103] (EE) Unable to initialize PCS database
[    15.103] (EE)   Missing PCS defaults file /etc/ati/amdpcsdb.default
[    15.103] (II) [KMS] drm report modesetting isn't supported.
[    15.103] (EE) open /dev/dri/card0: No such file or directory
[    15.103] (WW) Falling back to old probe method for modesetting
[    15.103] (EE) open /dev/dri/card0: No such file or directory
[    15.103] (II) Loading sub module "fbdevhw"
[    15.103] (II) LoadModule: "fbdevhw"
[    15.103] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.103] (II) Module fbdevhw: vendor="X.Org Foundation"
[    15.103] 	compiled for 1.15.1, module version = 0.0.2
[    15.103] 	ABI class: X.Org Video Driver, version 15.0
[    15.103] (**) FBDEV(2): claimed PCI slot 1@0:0:0
[    15.103] (II) FBDEV(2): using default device
[    15.103] (WW) Falling back to old probe method for vesa
[    15.103] (EE) Screen 0 deleted because of no matching config section.
[    15.103] (II) UnloadModule: "radeon"
[    15.103] (EE) Screen 0 deleted because of no matching config section.
[    15.103] (II) UnloadModule: "modesetting"
[    15.103] (II) FBDEV(0): Creating default Display subsection in Screen section
```

Please help.
Or should I create a new thread?

---

### Post by Bashing-om on 2016-03-30
wbloos; Hello;

The Radeon R9 280X was a special use case in linux . I think now it is stabilized and fully supported.
See:
[http://ubuntuforums.org/showthread.php?t=2244700](http://ubuntuforums.org/showthread.php?t=2244700)
[http://ubuntuforums.org/showthread.php?t=2278589](http://ubuntuforums.org/showthread.php?t=2278589)

As this may be unique to your hardware .. might be best to open a new thread if a problem continues and get QIII's attention as this card is of interest to him; possible he is still testing this card.

[INDENT][INDENT]we do what we can
[/INDENT][/INDENT]

---

### Post by wbloos on 2016-03-30
Thanks bashing-om , i've created a new thread [here]("http://ubuntuforums.org/showthread.php?t=2318951").
I really really want to get this fixed. I'm not sure how to get QIII's attention other than choosing a relevant title and tags.
Cheers :)

---

### Post by Bashing-om on 2016-03-30
wbloos; K

I meet ya in this new thread . IF QIII fails to pick up .. and we need his guidance, I will ping him for us.

[INDENT]we do what we can
[/INDENT]

---

