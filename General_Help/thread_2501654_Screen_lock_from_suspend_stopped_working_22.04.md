---
title: "Screen lock from suspend stopped working 22.04"
date: 2024-10-16
forum: General Help
---

### Post by maestrobwh1 on 2024-10-16
It has been a long while since I have needed to ask for help.  Have been using Ubuntu since 6.04, Dapper.

I have been running Ubuntu on a Mac Air 7.2 for a long while.  Currently, my system is 22.04 and it has been working well for over a year.  Recently after some upgrade, I lost my screen locking when suspending my machine.  All the relevant items are ticked in System Settings.  I used dconf-editor just to check those things were true.  I spend over an hour searching the web for similar issues including "Ask Ubuntu."  There are some similar posted issues and I tried those suggestions but most of them were entering command line items that can be done with dconf-editor, although I did them anyway to no avail.  I copied my partition to a blank disk, then attempted an upgrade to 24.04 and it borked although I recovered the upgrade from terminal with a  dpkg --configure -a and then also finished the upgrade from there... got to a desktop after a reboot and the issue still was there!  Close the lid... wait a few minutes or hours, it does go to sleep, but when I open the lid, it goes right to my desktop.  I did eventually restore my 22.04 install because there were some quirks with the upgrade that seemed buggy.

I only have lightdm installed.  I had both that and gdm3.  I tried one over the other and the issue persists so it is not a conflict between the two.

I did a "journalctl --no-tail > test.log" and looked there after also just logging out, then trying to suspend from there.  What happens then is I am indeed logged out with the lightdm greeter and when I choose "suspend" from the upper right corner, the screen does go completely dark, the Apple logo on the lid shuts off but about a second later, it wakes back up.

So I can either lock the screen OR suspend, but NOT BOTH?

Even though I have been using Ubuntu for 18 years or so, I can't really decipher the results of journalctl.  When done in terminal, there were a few red flags regarding scanning on my wifi adapter but nothing relating to what looks like the issue I am working with here.  Attached first few lines and last moments of journalctl in a text file in my reply below.

**EDIT: if I log out (not lock the screen via the menu, but actually log out) the machine will suspend as well, so my temporary solution is to just to log out, then close the lid.  **

---

### Post by maestrobwh1 on 2024-10-16
edited (shortened) results of journalctl attached

---

### Post by maestrobwh1 on 2024-10-19
After more digging, I found this:

```
root@brian-mac-air:/usr/local/bin# echo l > /proc/sysrq-trigger
root@brian-mac-air:/usr/local/bin# dmesg
```
> >>
[   11.263036] UBSAN: array-index-out-of-bounds in /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:1934:4
[   11.263046] index 2 is out of range for type 'ether_addr [1]'
>>
[ 2407.454510] CPU: 2 PID: 1505 Comm: Xorg Tainted: P           OE      6.8.0-47-generic #47~22.04.1-Ubuntu
[ 2407.454520] Hardware name: Apple Inc. MacBookAir7,2/Mac-937CB26E2E02BB01, BIOS 489.0.0.0.0 10/07/2023
[ 2407.454524] RIP: 0033:0x756b27365eb8
[ 2407.454545] Code: fc 41 bf 01 00 00 00 45 0f 44 e7 41 39 d4 45 89 e7 44 0f 47 e2 44 0f af e6 45 39 e1 45 0f 42 cc e9 46 ff ff ff 0f 1f 44 00 00 <83> 3c 24 05 0f 84 a6 05 00 00 41 83 fd 01 0f 84 24 07 00 00 41 83
[ 2407.454552] RSP: 002b:00007ffc33b59e10 EFLAGS: 00000246
[ 2407.454559] RAX: 0000000000000001 RBX: 000061a7c0ddc2a0 RCX: 0000000000000004
[ 2407.454565] RDX: 0000756b27c12d20 RSI: 0000000000000001 RDI: 0000756b27c10f20
[ 2407.454570] RBP: 00007ffc33b59f10 R08: 0000000000000001 R09: 0000000000000004
[ 2407.454575] R10: 0000000000000010 R11: 0000000000000001 R12: 00000000000000c0
[ 2407.454581] R13: 0000000000000000 R14: 0000000000000000 R15: 0000000000000001
[ 2407.454586] FS:  0000756b28c2ea80 GS:  0000000000000000
[ 2407.454592] NMI backtrace for cpu 3 skipped: idling at intel_idle+0x72/0xe0
[ 2407.454614] NMI backtrace for cpu 1 skipped: idling at intel_idle+0x72/0xe0

root@brian-mac-air:/usr/local/bin# journalctl -k | grep taint
> Oct 19 08:06:39 brian-mac-air kernel: wl: loading out-of-tree module taints kernel.
Oct 19 08:06:39 brian-mac-air kernel: wl: module license 'MIXED/Proprietary' taints kernel.
Oct 19 08:06:39 brian-mac-air kernel: Disabling lock debugging due to kernel taint
Oct 19 08:06:39 brian-mac-air kernel: wl: module verification failed: signature and/or required key missing - tainting kernel
Oct 19 08:06:39 brian-mac-air kernel: wl: module license taints kernel.

---

### Post by Norm24 on 2024-10-20
For me it was just the opposite,can't stand having screenlock enabled after suspend so I set the value at false.I prefer to manually lock the screen.

Open dconf-editor:
```
/org/gnome/desktop/suspend/lock-enabled [COLOR="#FF0000"]true[/COLOR]
```

---

### Post by maestrobwh1 on 2024-10-20
Peculiar for me but the folder suspend is missing from /org/gnome/desktop/ when I open dconf-editor.  I do have "screensaver" in that submenu and there is where I find the lock on suspend... it is set to true.  It is just an odd thing.  I can log out, and if I close the lid, it suspends.  I can close the lid and it suspends but does not lock, but if I lock the screen from the menu, it does not suspend.  My workaround is to log out, then close the lid.  It offers security and suspend.  Honestly, it is not a huge deal but it just started not locking AND suspending when I close the lid.

---

### Post by Norm24 on 2024-10-20
> **maestrobwh1 said:**
> Peculiar for me but the folder suspend is missing from /org/gnome/desktop/ when I open dconf-editor.  I do have "screensaver" in that submenu and there is where I find the lock on suspend... it is set to true.  It is just an odd thing.  I can log out, and if I close the lid, it suspends.  I can close the lid and it suspends but does not lock, but if I lock the screen from the menu, it does not suspend.  My workaround is to log out, then close the lid.  It offers security and suspend.  Honestly, it is not a huge deal but it just started not locking AND suspending when I close the lid.

For me using Mate I simply add Lock Screen to the panel and that's it.Click on the launcher and the screen locks and I the close lid,come back I open the lid and unlock it with my password.But for the most part I just don't like having to use my password to unlock the screen every time I close the lid,having the Lock Screen launcher in the panel allows me to lock the screen when I want to.

---

### Post by maestrobwh1 on 2024-10-21
The issue I am running into is that I can indeed lock the screen but then the laptop doesn't suspend when the lid is closed or if the suspend option is selected at the screen to log back in, it will "blink" at me and wake right back up. 

From the desktop, if i close the lid or choose suspend, it does suspend, just like I want.  

The only option I have and I guess it is okay for now is to actually log out.  If I log out and get the screen to log back in (the greeter), it will indeed suspend.  It is such a peculiar issue.  LOCKING prevents suspend.  I generally, and I don't know why, close my programs before closing a lid on a laptop so I'll live it it.  I spent entirely too much time doing down rabbit holes, and I am not even seeing any errors in any logs.  Honestly, my working desktop is an upgrade from a while ago from 20.04... and even after the upgrade, it would lock the screen and suspend when I closed the lid.  This is a very recent issue within the past few weeks.

---

### Post by Norm24 on 2024-10-23
One of my other other laptops is a Mac Air 6.2 running 22.04 Mate and I can't recreate your issue with it.I can manually lock it and close the lid and it suspends.With lock-enabled set to true I can close the lid and it suspends.Same on my Dell Latitude E7450 running Mate 24.04.

---

### Post by maestrobwh1 on 2024-10-27
So it must be a desktop GUI issue.  Odd thing because I don't get any errors anywhere that I look.

---

### Post by maestrobwh1 on 2024-10-27
Before marking this as solved, it may be helpful to determine WHY this works on 22.04 and the second, this time un-failed second attempt to upgrade to 24.04.  I just found this after what seems to be a very long search for a fix:

[https://askubuntu.com/questions/1231910/screen-does-not-lock-on-suspend](https://askubuntu.com/questions/1231910/screen-does-not-lock-on-suspend)

See the above if anyone is needing a fix to a similar issue.

The fix is to add a service that runs this script (again, see link to get the details):

```
#!/bin/sh
export XDG_SEAT_PATH="/org/freedesktop/DisplayManager/Seat0"
dm-tool lock
```

So now when I close my lid, the computer suspends (that never stopped working as long as i did not try to manually lock the screen), and when I wake it, the desktop does flash for a second, then the lock screen shows up.  Oddly, this happens with a fresh install of Ubuntu Budgie on a different partition and I thought it was odd that the suspended desktop would show for a second, if that, then the lock screen would show up, and that was not my doing.  It is just how it seems to work after a fresh install.

It is an acceptable "fix" BUT again, seeing if this might help someone determine what is happening.

---

### Post by maestrobwh1 on 2024-10-29
Did a chroot from a different Ubuntu partition and based on some other random research, I did

```
apt install --reinstall ubuntu-desktop^
```

The ^ forced all related packages to be downloaded, installed and configured.  I removed the service in the above post.  The machine behaves appropriately now.

---

