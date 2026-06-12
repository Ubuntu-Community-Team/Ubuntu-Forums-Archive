---
title: "Mythtv can't find tv card"
date: 2006-10-29
forum: General Help
---

### Post by bradcarr on 2006-10-29
Fresh install of Edgy 

Went by [http://www.parker1.co.uk/mythtv_ubuntu.php](http://www.parker1.co.uk/mythtv_ubuntu.php)

When I get to the part where I choose my TV card no matter what card I choose 
On the line that says        Probed info:  Failed to open 
I have installed Knoppmyth with no problem on the same box.
Any ideas on how to fix are greatly appreciated

THANKS

---

### Post by superm1 on 2006-10-30
What TV card are you using?

How did you setup the drivers for this TV Card?

If its IVTV, follow this wiki page: [https://wiki.ubuntu.com/Install_IVTV_Edgy](https://wiki.ubuntu.com/Install_IVTV_Edgy)

If its pcHDTV 2k,3k, did you install the firmware?

If its supported by 2.6.17 kernel dvb drivers, what does dmesg tell you?

If its another card, what card?

---

### Post by bradcarr on 2006-10-31
THANKS superm1

I am very new to ubuntu and Myth 

It was the IVTV that wasn't installed. Installed it, went in to setup and it found the card. 

but I got another question. When I scan for channels the highest channel it finds is 13. If I try to watch only thing higher all I get is snow. I have regular analog cable. Any ideas ?
 
Oh ya, by the way I have a PVR-350

---

### Post by tjw26 on 2006-11-02
Hi - I'm having a similar problem using a Hauppauge Win Nova-T DVB-T card that is supported by the Linux kernel drivers and works fine in Mplayer and Kaffeine.

Any suggestions welcomed as to how I can get past this - failed to open message.

Should I be looking for in DMESG given that my card actually works in other software?  Are there permission issues in /dev I need to check?

Thanks

---

### Post by superm1 on 2006-11-02
Permissions are usually the thing to blame for things like that.

Check /dev/dvb0/adapter0/*

```

mythtv@mythdell:/dev/dvb/adapter0$ ls -alh
total 0
drwxr-xr-x 2 root root     120 2006-09-16 23:09 .
drwxr-xr-x 3 root root      60 2006-09-16 23:09 ..
crw-rw---- 1 root video 212, 4 2006-09-16 23:09 demux0
crw-rw---- 1 root video 212, 5 2006-09-16 23:09 dvr0
crw-rw---- 1 root video 212, 3 2006-09-16 23:09 frontend0
crw-rw---- 1 root video 212, 7 2006-09-16 23:09 net0
```

Everything should be set to the video group having read/write access.

The mythtv user should be a part of the video group as well.

```
mythtv@mythdell:/dev/dvb/adapter0$ cat /etc/group | grep video
video:x:44:mythtv

```

---

