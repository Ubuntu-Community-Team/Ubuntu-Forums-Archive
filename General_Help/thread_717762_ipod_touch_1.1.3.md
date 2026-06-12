---
title: "ipod touch 1.1.3"
date: 2008-03-07
forum: General Help
---

### Post by xjgnsdof on 2008-03-07
I am well aware of the wiki on mounting iPod Touches and iPhones, but I get the following output in Terminal when I input "ipod-touch-mount": 

"ssh: : Name or service not known"

What's wrong? I have the right packages installed, and SSH is on and enabled on the Touch.

---

### Post by Metaljaz on 2008-03-07
Read through this thread:

[http://ubuntuforums.org/showthread.php?p=4443737](http://ubuntuforums.org/showthread.php?p=4443737)

---

### Post by xjgnsdof on 2008-03-07
```

emones@Gavel1:~$ sudo gedit /usr/share/ipod-convenience/mount-umount
emones@Gavel1:~$ ipod-touch-mount
root@192.168.1.7's password: 
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option

```

Still not mounting...

---

### Post by xjgnsdof on 2008-03-11
up

---

### Post by xjgnsdof on 2008-03-12
up

---

### Post by xjgnsdof on 2008-03-12
I have finally synched my iPod Touch in gtkpod. It's really quite simple, but the wiki instructions aren't very well written. As such, I think I owe it to the community to clarify them, at least for my iPod Touch.

INSTRUCTIONS FOR MOUNTING JAILBROKEN 1.1.3 IPOD TOUCH
1. Follow the instructions at the[ official wiki page]("https://help.ubuntu.com/community/PortableDevices/iPhone#head-2324e37d080ca00c9738c8653562c84872ab4a72"), stopping right after you complete step 4.

2. Input the following: ```
sudo gedit /usr/bin/iphone-mount
```

3. Find the following section of code, roughly around line 66
```
#Mount our Music Directory
#work around if its 1.1.3+
if ssh root@IPADDRESS test -d /var/mobile; then
```

where"IPADDRESS" = an actual IP address
4. Change this IP address to "$IPADDRESS" without the quotation marks.
5. Make sure that the /media/ipod/ directory is completely empty, whether it be through Nautilus or in the command line
6. Run the following to mount your iPod Touch: ```
ipod-touch-mount
```

I feel kind of weird going from having no clue how to mount my iPod Touch to claiming that I can write better instructions, but such is learning. Let me know if you can finally mount and sync your jailbroken 1.1.3 iPod Touches.

---

