---
title: "Delete a Read Only File"
date: 2018-08-28
forum: General Help
---

### Post by shane_faulkinbury2 on 2018-08-28
Okay, for reasons of my own I'm trying to get rid of everything Google.  I did a search for evrything Google on my hard drive and deleted everything using - ```
rm -rf -r
```

The only problem I have is with deleting 8 files.  The 8 files show as "read only" files.  I'm of course trying as root, but the computer still won't do it.  It says similar to this - ```
cannot remove 'x-google-video-pointer.xml': Read-only file system
```

Is there anything I can do?

---

### Post by HermanAB on 2018-08-28
That is not a read only file.

It is a read only file system.

Big diff.

---

### Post by ank2 on 2018-08-28
Yes, whole file system.

He should (as root) trype

mount

and list here.

---

### Post by oldos2er on 2018-08-28
You need to mount the partition read/write.  What file system is it using?

---

### Post by shane_faulkinbury2 on 2018-08-28
I type mount and then the command and get this - ```
/var/lib/snapd/snaps/large-pcap-analyzer_31.snap on /snap/large-pcap-analyzer/31 type squashfs (ro,nodev,relatime,x-gdu.hide)
```

---

### Post by ank2 on 2018-08-28
> **shane_faulkinbury2 said:**
> I type mount and then the command and get this - ```
/var/lib/snapd/snaps/large-pcap-analyzer_31.snap on /snap/large-pcap-analyzer/31 type squashfs (ro,nodev,relatime,x-gdu.hide)
```

Yes, it's read-only as the **ro **says.

As root type
[B]
mount -o remount,rw /snap/large-pcap-analyzer/3
[/B]
If this is successful you don't get any feedback. If so, open the **/etc/fstab as root** and look for this line. IF it has a **ro** change that to **rw** and save it. Then all will be fine on the next and all following reboots.

---

### Post by Holger_Gehrke on 2018-08-28
That's a snap. snaps are stored in squashfs. quote from 'man mksquashfs': "Squashfs  is  a  highly  compressed **read-only** filesystem for Linux.". You can't remount a squashfs writeable.

Holger

---

### Post by shane_faulkinbury2 on 2018-08-28
So what can I do?  I have to be able to get rid of them somehow!

---

### Post by shane_faulkinbury2 on 2018-08-28
ank2, this is what I got - ```
root@none-HP-Compaq-8200-Elite-SFF-PC:/home/none# 
root@none-HP-Compaq-8200-Elite-SFF-PC:/home/none# mount -o remount,rw /snap/large-pcap-analyzer/3
mount: /snap/large-pcap-analyzer/3: mount point does not exist.
```

---

### Post by DuckHook on 2018-08-28
Please note that the helpers here have no idea what you've done with your system, what you've installed/changed/customized etc. I don't use snap packages&#8212;whereas you obviously do&#8212;so am just applying very general guidelines here, but it seems you've installed a snap package called large-pcap-analyzer at some point in the past. I have no idea what this package does. However, to get rid of its footprint, obviously, you would have to remove it.

As an aside that may have relevance to your decision-making process (since you don't tell us what is motivating you), Google-authored code permeates the Linux-sphere and it is hardly possible to function in the Linux ecosystem without finding oneself using some of it. As general end users of a distro like Ubuntu, it is downright impossible to avoid it. For example, since Google personnel are active contributors to kernel development, some of it is bound into the kernel itself.

---

### Post by shane_faulkinbury2 on 2018-09-06
Duckhook and others, sorry, but I've had a rather busy work week!  I don't care about Google authored packages, but specific Google packages.  I've had them completely removed in the past, but I must have unstalled a snap package.  I just wonder what it was.  Is there anyway of finding out?  I ask because I've had them totally removed on 16.04.2, but now I have 18.04!

---

### Post by lordfrikk on 2018-09-07
If you just randomly delete files with Google in name I think that's a good way to make (some parts) of your system not working. Just remove the offending packages wholesale otherwise you're going to get into trouble.

---

### Post by Holger_Gehrke on 2018-09-07
You might want to be careful not to throw out the baby with the bathwater in this case. 'large-pcap-analyzer' is a tool for analysing network traffic captured with wireshark. The extension '.xml' of the file tells us it should be (somewhat human-readable) data. It's probable that this data is used by the program to identify traffic to and from google-video (youtube ...).

And I have to agree with DuckHook, Google uses Linux a lot and has contributed heavily to the kernel and many other projects. It's probably not possible to remove everything touched by Google from a Linux system and still have it work.

Holger

---

