---
title: "Ubuntu 7.10 Won't Boot"
date: 2007-09-14
forum: General Help
---

### Post by The_PhAnT0m on 2007-09-14
I tried upgrading Ubuntu 7.04 to 7.10. Everything seemed to work fine. When I restarted it, it wouldn't boot. Everytime I try to boot, it just hangs at some random place in the boot sequence. Twice I was able to get Gnome to start but all that appeared was the cursor and then it hung. I can USUALLY boot it in recovery mode. Sometimes it hangs at some random place in recovery mode too. I have absolutly no clue were to start looking for the problem. Any help would be much appreciated.

The_PhAnT0m

---

### Post by thadeoc on 2007-09-14
i experienced a similar problem after the latest kernel update, my laptop would hang in the "configuring network interfaces" stage of the boot.
to fix this, edit the /etc/network/interfaces file in recovery mode, and comment it so it looks like this:
<code>

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

..all further lines are commented out with #

</code>

then try restarting and see if that works

---

### Post by rsambuca on 2007-09-14
I think if you "have no idea where to start looking" for a problem, you should definitely be sticking with Feisty, 7.04.  

The newer version, 7.10 Gutsy Gibbon, is still alpha software, and has known bugs.  It is more for testing and development.

---

### Post by The_PhAnT0m on 2007-09-14
@thadeoc:
 I tried your suggestion, nothing changed.

@sambuca
Your probably right. But I use Linux mostly to learn, which is why I tried upgrading. Either way I would like to recover my system before resorting to a reinstallation. I don't think you quite understand me, the boot just hangs at random places throughout the boot sequence. Though the more I have tried it, the more I notice a trend. Trying to boot normally, it USUALLY hangs at either "loading hardware drivers" or "Starting posting daemen." Its hung at other places occasionally too. Using recovery mode, it usually hangs at either "setting the system clock"  or "input: SynPS/2 Syneptics TouchPad as /class/input/input3." Again it doesn't always crash there, just usually. Out of the two, it more commonly crashes at "input..." So if you have any ideas just tell me. Next time I'll remember not to upgrade to an alpha version.. or not. :)

---

### Post by rsambuca on 2007-09-14
Sorry, wasn't trying to insult you or anything.  It's just that you posted in the general help area.  Perhaps a mod can move this to the Gutsy section when they have a chance.

Anyways, back to your problem.  I find it strange that it is hanging at different spots in the boot up sequence.  You might start by checking your /var/logs files to see what is going on there.  At least that might give us a better idea of what is going on.

---

### Post by The_PhAnT0m on 2007-09-14
No offense taken. Thats the problem though, its seemingly random crashes. Otherwise I could have figured it out myself. Here is one log of the boot process. Its very difficult to get to these files so what exactly do you think we should be looking for? For the record, I am using an HP Pavilion laptop.

[http://purpletrees.googlepages.com/dmesg.0]("http://purpletrees.googlepages.com/dmesg.0")

---

### Post by rsambuca on 2007-09-14
Sorry, I don't see anything obvious in there, other than a minor apci error.

---

### Post by The_PhAnT0m on 2007-09-14
I guess I'll just reinstall Feisty, its not worth the effort... sigh... thanks anyway.

---

### Post by g2g591 on 2007-09-14
don't worry, my upgrade to gutsy borked too,( but it was only some packages and I had enough intact to reboot and fix it) if you still want to try gutsy, I recommend downloading/installing a daily build iso so you don't have 300megs of updates (thats how I reinstalled after a Mandrivia install borked)

---

### Post by The_PhAnT0m on 2007-09-15
Well for some reason none of my Ubuntu live CDs will work so I'm back to trying to fix gutsy for the moment. I starting to suspect AppArmor MIGHT have something to do with it. According to Apt-Get its not "fully installer or removed."

When I try to remove it, something like this comes out.
```

Removing apparmor,
Unloading AppArmor profiles -  failed, is AppArmor loaded?: Failed.
invoke-rc.d: initscript apparmor, action "stop" failed.
dpkg: error processing apparmor(-remove)
   subprocess pre-removal script returned error exit status 1
$Loading AppArmor module: Failed
invoke-rc.d: initscript apparmor "start" failed.
dpkg: error while cleaning up:
   subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
   apparmor
E: Sup-process /usr/bin/dpkg returned an error code (1)
```

When I try to install it, something similar is outputted. I had never heard of AppArmor before Gutsy. So I guess I'll have to do some research. Anyone got any ideas?

---

### Post by g2g591 on 2007-09-15
wow, now apparmor failed to upgrade for me also, with a simaler error, leaving my recent kernel update unbootable (backup still works)

(Reading database ... 105682 files and directories currently installed.)
Preparing to replace apparmor 2.1+961-0ubuntu4 (using .../apparmor_2.1+961-0ubuntu5_i386.deb) ...
Unpacking replacement apparmor ...
Setting up apparmor (2.1+961-0ubuntu5) ...
Installing new version of config file /etc/apparmor/rc.apparmor.functions ...
update-initramfs: deferring update (trigger activated)
Loading AppArmor profiles /sbin/apparmor_parser: Unable to add "/usr/lib/cups/backend/cups-pdf".  Profile doesn't conform to protocol
 Profile /etc/apparmor.d/usr.sbin.cupsd failed to load
: Failed.
invoke-rc.d: initscript apparmor, action "start" failed.
Reloading AppArmor profiles /sbin/apparmor_parser: Unable to repl    ace "/usr/lib/cups/backend/cups-pdf".  Profile doesn't conform to protocol
 Profile /etc/apparmor.d/usr.sbin.cupsd failed to load
: Failed.
invoke-rc.d: initscript apparmor, action "reload" failed.

---

### Post by The_PhAnT0m on 2007-09-15
Interesting... I still am trying to learn some more about AppArmor. On my Desktop it worked absolutely flawlessly though. I wonder why AppArmor won't start though. Its like Ubuntu can't use it or its not there. Really weird. All my kernels are unbootable. I have tried three different versions.

---

### Post by The_PhAnT0m on 2007-09-15
@g2g591: What kind of printers do you have? If you have printers, what did you need to do to get them to work?

---

### Post by The_PhAnT0m on 2007-09-15
I have run into a weird roadblock. None of my 3 Ubuntu LiveCDs (Ubuntu 7.04, Ubuntu 7.04, Ubuntu 7.10) will boot. But my Gentoo 2007.0 DVD and my SystemRescueCd work perfectly. Windoze :evil: works fine too. According to the Ubuntu CDs' self checks, they are all in perfect condition. Any clue why they don't work? I think this is getting to be more serious than a simple reinstall.

Note: I have no clue if this as any effect on anything but ever since I have installed Ubuntu, it said something about a BIOS bug at the very beginning of the boot. It has always flashed by to quickly for me to get a clear look at it but I think that is what it said.

---

