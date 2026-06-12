---
title: "Kubuntu 7.04 vanilla install crashes after login"
date: 2007-07-30
forum: General Help
---

### Post by immesys on 2007-07-30
After eventually getting kubuntu to install, I am now having problems where it will not get into KDE successfully.

Originally, it would not load the window manager. After upgrading everything, it now gets in but hangs within a few seconds rendering the computer completely oblivious to input.

I've looked at all the log files and can't seem to find anything other than a couple of these, I don't know if they are ominous or not:

```

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```


My hardware listing as well as kdm.log, daemon.log and dmesg are attatched

Please help! I've never had issues with ubuntu before and 7.04 is giving me a lot of hassles!

Thanks!

---

### Post by immesys on 2007-07-30
I found that the X errors were because 7.04 comes with wacom input devices by default in xorg.conf. If you remove everything relating to wacom tablets it stops giving that error.

The problem remains however. My KDE is hanging my entire pc straight after login... has nobody else had this problem?

---

### Post by immesys on 2007-07-30
Found the problem. There's a bug in 7.04 with the cpu-speed throttling of certain AMD CPU's. By chmodding /etc/init.d/powernowd to 000, I seem to have stopped the hangs on startup.

---

