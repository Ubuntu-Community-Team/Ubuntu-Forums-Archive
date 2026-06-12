---
title: "Computer unexpectingly shutting down. Don't know how to read syslog..."
date: 2020-12-11
forum: General Help
---

### Post by meldane on 2020-12-11
Hi... My computer keeps on shutting down unexpectedly, after a few minutes or a few hours. And I am struggling to find to reason why. It doesn't appear to be linked to high temperature being reached in any case.I went to have a look at my syslog, but I wouldn't really know how to spot something being wrong.I get those lines, for instance :
```
Dec 11 10:23:37 kubisda systemd[1]: Starting Update UTMP about System Boot/Shutdown...
```
```
Dec 11 10:23:37 kubisda apparmor.systemd[810]: Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
```
```
Dec 11 10:23:37 kubisda systemd[1]: Finished Update UTMP about System Boot/Shutdown.
```
Would anyone know how to identify what's wrong ?

---

### Post by DuckHook on 2020-12-11
Welcome to the forums, meldane,

Please refrain from using nonstandard fonts or styles. They are hard to read on small screens or mobile devices. Also, please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by VMC on 2020-12-12
What make & model of computer?

---

### Post by meldane on 2020-12-12
Thanks for the advice and for editing my message, DuckHook, that's kind of you.

I didn't realize I has used a special font. I just copied and pasted the text I had just posted in a Linux group chat room, until I though a forum was maybe more appropriate to ask for help in resolving my issue...

OK, I'll be careful to keep my message clear from now ! :)

---

### Post by meldane on 2020-12-12
> **VMC said:**
> What make & model of computer?

Thanks for your answer, VMC.

Hmm... That's a desktop computer. I assembled it 10 years ago and bought all the parts separately. 

Here are the main info :

Operating System: Kubuntu 20.04
KDE Plasma Version: 5.18.5
KDE Frameworks Version: 5.68.0
Qt Version: 5.12.8
Kernel Version: 5.4.0-56-generic
OS Type: 64-bit
Processors: 4 × Intel® Core™ i3 CPU 530 @ 2.93GHz
Memory: 7,6 GiB of RAM

Are you asking for the motherboard model more specifically ?

---

### Post by deadflowr on 2020-12-12
```
journalctl -b -1 | tail -n 50
```
this will output the last 50 lines of the journal log from the last boot.
It should show the last things to happen before it shutdown.
You can forgo the -n 50 and just run with only tail which will show the last 10 lines.

If the last boot was fine or shutdown properly,
you can change -1 to an earlier boot, like
-2 for a boot 2 boots earlier
-3 for 3 boots earlier
and so on.

---

### Post by VMC on 2020-12-12
> **meldane said:**
> Thanks for your answer, VMC.

Hmm... That's a desktop computer. I assembled it 10 years ago and bought all the parts separately. 

Here are the main info :

Operating System: Kubuntu 20.04
KDE Plasma Version: 5.18.5
KDE Frameworks Version: 5.68.0
Qt Version: 5.12.8
Kernel Version: 5.4.0-56-generic
OS Type: 64-bit
Processors: 4 × Intel® Core™ i3 CPU 530 @ 2.93GHz
Memory: 7,6 GiB of RAM

Are you asking for the motherboard model more specifically ?
No. I'm having similar issue, but different hardware.

---

### Post by guiverc on 2020-12-12
I'd look in systemd logs as @deadflwr already suggested, however if they show nothing, and it's an old box like mentioned I'd likely explore hardware (*you mentioned temperature, which you said was okay*).

After temperature, I'd think about the PSU.  Was it some action you did that caused an extra drain on the PSU (*power supply unit*) that caused it to reach the point where *PWR_OK * signal dropped & thus the motherboard may just shutdown (*OS isn't involved*). Motors use power, so spinning of drives, cd/dvd/etc, or combination of heat (*thus fans spinning faster*) & drives/cd/dvd or other devices...

Just a thought (*thus maybe wild goose chase*)  I'd usually test this theory out by using a *live* system, and using whatever hardware the box has in a way that will cause *stress* on PSU & look for inconsistent voltages and the potential for limit to be reached and PWR_OK to drop (ie. the usually wire that tells the motherboard/cpu that reliable power is available & motherboard/box can operate).  Systemd logs will contain no clue; just end unexpectedly at poweroff time so the lack of detail itself is a minor clue too.

---

### Post by Autodave on 2020-12-13
That definitely sounds like a power supply issue.  If you have a lot of USB devices connected, disconnect all but what is needed and try that for awhile.  Occasionally, I have seen spinning hard drives cause that issue.

---

### Post by meldane on 2021-02-12
Hi all, 

[B]Thanks a lot for your answers. I haven't been too reactive because I used an other computer in the meantime, but I am now back to the defective one. Yeah I guess I better change the PSU... That seems to be it.
[/B]
> **deadflowr said:**
> ```
journalctl -b -1 | tail -n 50
```
this will output the last 50 lines of the journal log from the last boot.
It should show the last things to happen before it shutdown.
You can forgo the -n 50 and just run with only tail which will show the last 10 lines.

If the last boot was fine or shutdown properly,
you can change -1 to an earlier boot, like
-2 for a boot 2 boots earlier
-3 for 3 boots earlier
and so on.

**I did that though, and that's the outcome I got :**

> févr. 12 12:35:14 kubisda systemd[1]: Mounted POSIX Message Queue File System.
févr. 12 12:35:14 kubisda systemd[1]: Mounted Kernel Debug File System.
févr. 12 12:35:14 kubisda systemd[1]: Mounted Kernel Trace File System.
févr. 12 12:35:14 kubisda systemd[1]: Finished Create list of static device nodes for the current kernel.
févr. 12 12:35:14 kubisda kernel: EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
févr. 12 12:35:14 kubisda systemd[1]: Finished Remount Root and Kernel File Systems.
févr. 12 12:35:14 kubisda systemd[1]: Finished Uncomplicated firewall.
févr. 12 12:35:14 kubisda systemd[1]: Condition check resulted in Rebuild Hardware Database being skipped.
févr. 12 12:35:14 kubisda systemd[1]: Condition check resulted in Platform Persistent Storage Archival being skipped.
févr. 12 12:35:14 kubisda systemd[1]: Starting Load/Save Random Seed...
févr. 12 12:35:14 kubisda systemd[1]: Starting Create System Users...
févr. 12 12:35:14 kubisda kernel: lp: driver loaded but no devices found
févr. 12 12:35:14 kubisda systemd[1]: Finished Load/Save Random Seed.
févr. 12 12:35:14 kubisda systemd[1]: Finished Create System Users.
févr. 12 12:35:14 kubisda systemd[1]: Starting Create Static Device Nodes in /dev...
févr. 12 12:35:14 kubisda kernel: ppdev: user-space parallel port driver
févr. 12 12:35:14 kubisda systemd[1]: Finished Load Kernel Modules.
févr. 12 12:35:14 kubisda systemd[1]: Mounting FUSE Control File System...
févr. 12 12:35:14 kubisda systemd[1]: Mounting Kernel Configuration File System...
févr. 12 12:35:14 kubisda systemd[1]: Starting Apply Kernel Variables...
févr. 12 12:35:14 kubisda systemd[1]: Mounted FUSE Control File System.
févr. 12 12:35:14 kubisda systemd[1]: Mounted Kernel Configuration File System.
févr. 12 12:35:14 kubisda systemd[1]: Finished Create Static Device Nodes in /dev.
févr. 12 12:35:14 kubisda systemd[1]: Starting udev Kernel Device Manager...
févr. 12 12:35:14 kubisda systemd[1]: Finished Set the console keyboard layout.
févr. 12 12:35:14 kubisda systemd[1]: Finished Apply Kernel Variables.
févr. 12 12:35:14 kubisda systemd[1]: Reached target Local File Systems (Pre).
févr. 12 12:35:14 kubisda systemd[1]: Mounting Mount unit for chromium, revision 1475...
févr. 12 12:35:14 kubisda systemd[1]: Mounting Mount unit for chromium, revision 1479...
févr. 12 12:35:14 kubisda systemd[1]: Mounting Mount unit for core18, revision 1944...
févr. 12 12:35:14 kubisda systemd[1]: Mounting Mount unit for core18, revision 1988...
févr. 12 12:35:14 kubisda systemd[1]: Mounting Mount unit for gnome-3-28-1804, revision 128...
févr. 12 12:35:14 kubisda systemd[1]: Mounting Mount unit for gnome-3-28-1804, revision 145...
févr. 12 12:35:14 kubisda systemd[1]: Mounting Mount unit for gtk-common-themes, revision 1513...
févr. 12 12:35:14 kubisda systemd[1]: Mounting Mount unit for gtk-common-themes, revision 1514...
févr. 12 12:35:14 kubisda systemd[1]: Mounting Mount unit for riot-web, revision 76...
févr. 12 12:35:14 kubisda systemd[1]: Mounting Mount unit for riot-web, revision 96...
févr. 12 12:35:14 kubisda systemd[1]: Mounting Mount unit for snapd, revision 10707...
févr. 12 12:35:14 kubisda systemd[1]: Mounting Mount unit for snapd, revision 11036...
févr. 12 12:35:14 kubisda systemd[1]: Finished udev Coldplug all Devices.
févr. 12 12:35:14 kubisda systemd-journald[378]: Journal started
févr. 12 12:35:14 kubisda systemd-journald[378]: Runtime Journal (/run/log/journal/25732baab27c458691fd261a1da8268a) is 8.0M, max 77.6M, 69.6M free.
févr. 12 12:35:14 kubisda systemd-modules-load[383]: Inserted module 'lp'
févr. 12 12:35:14 kubisda systemd-modules-load[383]: Inserted module 'ppdev'
févr. 12 12:35:14 kubisda systemd-modules-load[383]: Inserted module 'parport_pc'
févr. 12 12:35:14 kubisda systemd-sysctl[401]: Not setting net/ipv4/conf/all/promote_secondaries (explicit setting exists).
févr. 12 12:35:14 kubisda systemd-sysctl[401]: Not setting net/ipv4/conf/default/promote_secondaries (explicit setting exists).
févr. 12 12:35:14 kubisda systemd[1]: Starting Flush Journal to Persistent Storage...
févr. 12 12:35:14 kubisda systemd[1]: Started Journal Service.
févr. 12 12:35:14 kubisda systemd-journald[378]: Time spent on flushing to /var/log/journal/25732baab27c458691fd261a1da8268a is 14.943ms for 905 entries.


**It doesn't show anything unusual, does it ?**

---

### Post by meldane on 2021-02-12
> **guiverc said:**
> 

After temperature, I'd think about the PSU.  Was it some action you did that caused an extra drain on the PSU (*power supply unit*) that caused it to reach the point where *PWR_OK * signal dropped & thus the motherboard may just shutdown (*OS isn't involved*). Motors use power, so spinning of drives, cd/dvd/etc, or combination of heat (*thus fans spinning faster*) & drives/cd/dvd or other devices...


No, I only had Firefox opened with 4 tabs opened, and reading some articles, with Element (Matrix client software running quietly), and Thunderbird opened.
I wasn't even watching a video. No particular stress I could notice. No USB device attached.

---

### Post by HermanAB on 2021-02-12
Ten years ago...  You likely have bad power quality due to dry electrolytic capacitors in the PSU and motherboard, causing computational errors.

---

### Post by meldane on 2021-02-18
Oh right, thanks for your answer, Herman.

So changing the PSU is likely not to be enough... I will probably need to change the motherboard as well... :(

---

### Post by mastablasta on 2021-02-18
it is likely just a PSU issue.

change PSU first. buy one with enough power. buy a good one and at least a bronze one. if it doesn't resolve the issues on current build, you can always use it later when replacing the motherboard. i would get at least 450W so i can do even more upgrades later if needed. but you may be OK with 350 W bronze.

motherboard with bad capacitors usually locks up first or displays strange boot cycles while the capacitors get the proper charge.

i use single core CPU on old motherboard. the base pc is over 16 years old. if i am not mistaking, i am on 3rd PSU now.
i had issues on the other one with various old components. i changed PSU to 550 W and it was a bit better for a while, but then i continued to have strange behaviour. so we used the disk, connector cables and PSU from this old PC and built a new "gaming" PC with Ryzen 7 CPU. no issues since...  but my point is we could successfuly re-use new components form bad built on new build.

---

