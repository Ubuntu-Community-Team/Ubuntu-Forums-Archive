---
title: "Problems with the Hardware Abstraction Layer (HAL)"
date: 2007-07-07
forum: General Help
---

### Post by praxis22 on 2007-07-07
Hi,

I've just rebuilt the Kernel and now I'm getting HAL errors. Specifically, I boot into gnome and I get a popup error message:

**Internal Error**
Failed to initialize HAL!

It's not dbus related since dbus is working fine, but even if I do restart dbus, it fails to restart hald.

Then I try to start it manually I get:

```

sudo /usr/sbin/hald --daemon=no --verbose=yes
14:09:24.443 [I] hald.c:529: hal 0.5.9
14:09:24.443 [I] hald.c:594: Will not daemonize
14:09:24.443 [I] hald_dbus.c:4806: local server is listening at unix:abstract=/var/run/hald/dbus-y2bXkKNFI5,guid=c82cd048b56b795c08f97700468f9084
Runner started - allowed paths are '/usr/lib/hal:/usr/lib/hal/scripts:/usr/bin'
14:09:24.448 [I] hald_runner.c:299: Runner has pid 5123
14:09:24.448 [I] hald_runner.c:180: runner connection is 0x80936c8
14:09:24.449 [I] mmap_cache.c:251: cache mtime is 1183674298
*** [DIE] osspec.c:watch_fdi_files():349 : Unable to initialize inotify: Function not implemented 

```

More:
```

pidof hald
kieron@ubuntu7:~$ ps -p $(< /var/run/dbus/pid)
  PID TTY          TIME CMD
 4481 ?        00:00:00 dbus-daemon

```

I'm building this box for somebody else on an old 2Ghz P4 Northwood, in an ASRock P4V88+ Motherboard (VIA  Chipset, PT880 Northbridge, 8237 Southbridge) I've puled most of the stuff I don't need out, in an attempt to make it run faster. Any idea as to what I may have to add back in?

I notice that the CD-RW is acting up, it will take a CD and mount it, it just wont give it back when I press the button, I have manually tell it to eject the CD. 

This is with Kernel 2.6.21.5 on Feisty 7.04 (32bit)

Any ideas?

---

### Post by p_quarles on 2007-07-07
EDIT: Forget that. Just reread the question.

---

### Post by praxis22 on 2007-07-07
Looks like it's a known problem:

[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg354533.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg354533.html)

[i]Yes, looking at the source, the new upstream version seems to require a
kernel with inotify support now. This is an upstream issue of course,
and it would be kind if you could ask upstream to not require inotify.[/i]

From what I've read it looks like it's in the filesystems section, either that, or recompile glibc.  Failing that install an earlier version of hald:

[http://forums.gentoo.org/viewtopic-t-562640.html](http://forums.gentoo.org/viewtopic-t-562640.html)

I'll recompile first and see what happens.

---

### Post by praxis22 on 2007-07-07
Well, interestingly enough, I rebuilt the kernel again, including inotify support, and hald still bobs out with the same error:

However, if I subsequently try to restart dbus it just locks up the console:

```

 sudo /etc/init.d/dbus restart
 * Stopping System Tools Backends system-tools-backends                  [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Stopping system message bus dbus                                      [ OK ] 
 * Starting system message bus dbus                                      [ OK ] 
 * Starting Hardware abstraction layer hald                                     

```

Whereas before hald bombed out and the dbus restart completed.

I may take a look at a new version of hald.

**EDIT:** OK, looks like I just didn't wait long enough, it took a while and then exited with a different error:

```

run-parts: /etc/dbus-1/event.d/20hal exited with return code 2
 * Starting DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Starting network connection manager NetworkManager                    [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Starting network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Starting System Tools Backends system-tools-backends                  [ OK ] 

```

---

### Post by AstarothCY on 2007-09-16
bump, i am having the same problem, did you fix it?

---

### Post by praxis22 on 2007-09-17
yes, but I didn't fix the problem just avoided it.

I downloaded a new kernel, re-patched, and then configured from scratch not using the existing kernel config.

It's not quick, (actually very boring and time intensive) looking up all the assorted kernel subsystems, but it did, eventually work. 

It's basically trial and error.

---

### Post by AstarothCY on 2007-09-17
Did you follow a HowTo? If not, could you give a quick rundown of what you did, or at least the idea behind it so that I could replicate? I have a couple of things to try before this, as I mentioned in [this thread](http://ubuntuforums.org/showthread.php?t=491482&page=2) but I have a suspicion that they won't work, and frankly I would rather rebuild a kernel from scratch than reinstall Ubuntu and have to reconfigure all my apps.

---

### Post by praxis22 on 2007-09-17
Hi,

I just followed this thread:

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

Until step 7, then did "make menuconfig"

Then I went from there.

Beyond that it's just a matter of doing research about what all the underlying kernel subsystems are and whether you think you'll need them.

---

### Post by AstarothCY on 2007-09-17
Hah, great, that's exactly what I started doing last night... when I saw the config menu I just felt daunted and gave up. I suppose if it worked for you then it's worth trying out. I will keep you updated.

BTW Do you have any hardware similar to mine? Check the first page of the thread I linked above.

---

### Post by praxis22 on 2007-09-17
Hi,

I was building an old cast-off PC, from a 2.0Ghz P4 Northwood, an ASRock (V cheap, AGP) motherboard, 512Mb of RAM, and an ATI 6000 series AGP card. It's a low profile, passively cooled card. It was using an old 8Gb drive out of a first gen Xbox as a HD. worked OK.

I even got the embedded version of beryl working on it, 

Gave it to somebody who knew nothing about computers, and just wanted to access the web and online chat. Configured it for audio, and Skype, etc. Worked fine, he's never had a problem with it. Which is more than I can say for the XP install I gave him first.

---

### Post by AstarothCY on 2007-09-17
SOLVED by installing the gutsy HAL packages as described [here](https://launchpad.net/hal/+bug/92647). I also had to remove the gutsy kernel and reinstall the latest feisty kernel (20-16) and it boots fine. HOWEVER I still have other problems, I will make a new thread though since the problem has changed a lot. I will link the followup thread here when I make it.

---

### Post by jaybombalous on 2007-10-31
```
jasin@ubuntu:~$ sudo /usr/sbin/hald --daemon=no --verbose=yes
[sudo] password for jasin:
04:45:28.157 [I] hald.c:529: hal 0.5.9.1
04:45:28.157 [I] hald.c:594: Will not daemonize
04:45:28.157 [I] hald_dbus.c:4807: local server is listening at unix:abstract=/var/run/hald/dbus-6J7FRkjZFg,guid=5a888ef320dce8ac13192500472840a8
Runner started - allowed paths are '/usr/lib/hal:/usr/lib/hal/scripts:/usr/bin'
04:45:28.179 [I] hald_runner.c:299: Runner has pid 4174
04:45:28.179 [W] ci-tracker.c:200: Could not get uid for connection: org.freedesktop.DBus.Error.NameHasNoOwner Could not get UID of name 'org.freedesktop.DBus': no such name
04:45:28.179 [E] hald_dbus.c:4462: Cannot get caller info for org.freedesktop.DBus
04:45:28.179 [I] hald_runner.c:180: runner connection is 0x653660
04:45:28.228 [I] mmap_cache.c:251: cache mtime is 1193818574
*** [DIE] osspec.c:watch_fdi_files():349 : Unable to initialize inotify: Function not implemented 
```

So I suppose I need to recompile with** inotify** as well?

edit: re-compiling w/inotify worked

---

