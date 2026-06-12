---
title: "NFS shares not mounting"
date: 2019-07-24
forum: General Help
---

### Post by marcw on 2019-07-24
In my 18.04 desktop I've got 6 NFS shares to my Synology NAS that I start with fstab entries.  They've been working (mounting) fine for over a year.  Sometime in the past week or two these shares have stopped mounting at startup and reboot and I don't know why.  I have made no changes to anything except for periodic system updates via synaptic.  I'm not seeing any errors with dmesg.  I can run sudo mount -a and everything gets mounted fine:

192.168.0.33:/volume1/Music	/Music	nfs	defaults 0 0
192.168.0.33:/volume1/mdance	/mdance	nfs	defaults 0 0
192.168.0.33:/volume1/Video	/Video	nfs	defaults 0 0
192.168.0.33:/volume1/files	/files	nfs	defaults 0 0
192.168.0.33:/volume1/Photos	/Photos	nfs	defaults 0 0
192.168.0.33:/volume1/genealogy /genealogy nfs     defaults 0 0

Just for fun I modified the options with auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 but it made no difference.   I'd like to know what happened and how to get my shares auto-mounting correctly at start-up again.  Looking for suggestions.

---

### Post by SeijiSensei on 2019-07-24
Did the IP address of the NAS change? Does it have a static IP or get its address via DHCP? Any device running as a server should have a static IP.

---

### Post by marcw on 2019-07-24
It's reserved DHCP (the equivalent of static).  Like I mentioned, all my shares become available with sudo mount -a.

---

### Post by marcw on 2019-07-25
I just noticed a series of these errors in dmesg that I hadn't noticed earlier:
[    7.315404] FS-Cache: Duplicate cookie detected
[    7.315409] FS-Cache: O-cookie c=00000000a944c799 [p=000000000ad935c0 fl=222 nc=0 na=1]
[    7.315411] FS-Cache: O-cookie d=00000000f1ac6b94 n=00000000ea43b91d
[    7.315413] FS-Cache: O-key=[10] '040002000801c0a80021'
[    7.315421] FS-Cache: N-cookie c=00000000bd6f395e [p=000000000ad935c0 fl=2 nc=0 na=1]
[    7.315423] FS-Cache: N-cookie d=00000000f1ac6b94 n=00000000724c3800
[    7.315424] FS-Cache: N-key=[10] '040002000801c0a80021'
(and several more of the same)

I suppose it's possible that I'm running into this bug: [https://bugzilla.kernel.org/show_bug.cgi?id=200145](https://bugzilla.kernel.org/show_bug.cgi?id=200145)
I'm on kernel 4.18.0-25-generic.  Sure makes me wish I had saved some of my earlier kernels.

---

### Post by sevendogs1337 on 2019-07-25
Did nfs-common get uninstalled somehow? I have a synology NAS as well and that is the only package that is required to mount my NAS. It pulls in a couple of other things but I can't mount until I install that.

---

### Post by marcw on 2019-07-25
No, it's there.  But just to make sure something didn't go haywire I did a re-install of it.  Made no difference - the issue still exists.

---

### Post by sevendogs1337 on 2019-07-25
OK, just a shot in the dark, you never know...so, just did a quick google of your error msg but you probably have already done that: appears to be a kernel bug: [https://bugzilla.kernel.org/show_bug.cgi?id=200145](https://bugzilla.kernel.org/show_bug.cgi?id=200145)

That's a little disheartening.

EDIT - sigh, sorry, you posted that link already! Need more coffee...

---

