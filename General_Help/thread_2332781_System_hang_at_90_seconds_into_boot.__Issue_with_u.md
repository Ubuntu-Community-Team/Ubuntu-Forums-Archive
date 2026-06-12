---
title: "System hang at 90 seconds into boot.  Issue with: usb 3-9: device descriptor read/64"
date: 2016-08-03
forum: General Help
---

### Post by Drone4four on 2016-08-03
My system hangs for ~90 seconds at boot with some message indicating a problem with usb 3-9: device descriptor read/64, error -110.  [URL="http://pastebin.com/e8dUrUCR"]

Here[/URL] is my dmesg.

I looked up the error message on Google which[ turned up this entry on launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1389006") which isn't really related or helpful.

What could be my issue? 

Is there any other information I could provide to help you help me continue troubleshooting?

---

### Post by gordintoronto on 2016-08-04
What version of Linux? I used to get messages such as you describe before moving to Xubuntu 16.04 and Linux Mint 18.

---

### Post by jeremy31 on 2016-08-04
Please post results  for ```
lsusb
```

I think the issue is more related to this ```
[   92.653376] EXT4-fs (sdb2): mounting ext3 file system using the ext4 subsystem
```

---

### Post by Drone4four on 2016-08-06
> **gordintoronto said:**
> What version of Linux? I used to get messages such as you describe before moving to Xubuntu 16.04 and Linux Mint 18.
I'm running 64bit vanilla 16.04.

> **jeremy31 said:**
> Please post results for ```
lsusb
```
I think the issue is more related to this ```
[   92.653376] EXT4-fs (sdb2): mounting ext3 file system using the ext4 subsystem
```
Here it is:
```
$ lsusb
Bus 002 Device 002: ID 8087:8002 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:800a Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 045b:0210 Hitachi, Ltd 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 045b:0209 Hitachi, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

