---
title: "UUID=?? What happened to /dev/hda*?"
date: 2007-05-11
forum: General Help
---

### Post by jerremy-tamlin on 2007-05-11
I just upgraded to feisty and am wondering what happened to /dev/hda*

I see that fstab now uses UUID= Is this a hardware address? How do I find the address if I want to install a new hard drive?

One of the things I love about linux is that it's _Human Readable_ It might be in code but it's a language I can learn. Linux is supposed to give power to users. Thats why it's so much better than windows. I whole heartedly support the Ubuntu team making it user friendly and possible to never see a scrap of code, but please don't make it so that only IT wizzes can understand it's workings.

This: 4ca3dbf4-f7de-4211-b929-b8eb79afd031 Is Not something I can understand especially with no explanatory comment as to what it is.

Can someone tell me what the rational behind this change was and better still how to put /dev/hda* back. I can't run parted or anything else that directly works on my hard disks without it.

Thanks

---

### Post by m.musashi on 2007-05-11
I've been wondering the same thing. I do know that you can still use /dev/hda or whatever but it now defaults to using the UUID. I also know that if you change things the UUIDs get messed up. I changed some partitons and nothing worked anymore. I had to go in and use /dev/hdx to get it working again.

---

### Post by benanzo on 2007-05-12
I think most distributions are using the UUID (Universal Unique Identifier) in fstab and grub config to refer to specific disk partitions now.  The reason is that it makes moving disks around in your system easier because the UUID wont change, but the specific device file might (/dev/hda*) if you move it to a different IDE channel etc.  Device files are created dynamically and might change if you introduce a new disk to the system.  This would be bad if you set your / partition static in fstab or grub config as say /dev/hda1.  A situation could arise that moves that specific partition to /dev/hdb1 (or similar) which would cause grub to not be able to find your disk at boot time.  If you have a simple disk setup with just one or two disks that you don't move around it is fine to edit /boot/grub/menu.lst to refer to the device file instead of the UUID, but it is generally better to use the UUID.

---

### Post by Neobuntu on 2007-05-12
How about we don't use UUID for the one(s) GRUB calls then, BY DEFAULT?

---

### Post by strabes on 2007-05-12
The reason it uses UUIDs is because they don't change unless you change your partitions around. /dev/sdb1 can refer to more than one partition because you could plug in a drive and it would be /dev/sdb1, then you could unmount it and plug in a different one and it would also be /dev/sdb1. A UUID can only refer to a specific partition on a specific device. You'd run into trouble if you wanted different options for different devices in your fstab. To find UUIDs, run ```
ls -l /dev/disk/by-uuid/
```

---

### Post by heimo on 2007-05-12
> **Neobuntu said:**
> How about we don't use UUID for the one(s) GRUB calls then, BY DEFAULT?

From my grubs menu.lst, which was automatically created for me:
```
title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=d1af2f96-3235-493d-9363-9db6cd8438
dd ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```

So it's used to refer to root partition, but you still need to use grubs (hdX,Y) syntax to referring to devices.

---

### Post by jerremy-tamlin on 2007-06-04
Hmm... thats strange I don't seem to be subscribed automatically to threads that I post to anymore?
Didn't realize anyone had replied to my post.

Thanks for the explanations, I now think my problem might be a little bigger than I first thought.

My system doesn't have /dev/hd* entires at all anymore.

It has /dev/sda* and /dev/sdb* entries and links to them in /dev/disk/by-uuid/ But doing a locate for 'hda', 'hdb', etc. doesn't yield any results.

My system works and the install process detected my hd and partitions and setup everything fine but if I want to repartition or do anything else to my device I don't know where to find it.

Do you guys still have an entry /dev/hda, /dev/hda1, etc?

ie. if on the console/terminal you type
```
ls /dev/hd*
```
Do you get any results?

Thanks

---

### Post by vanadium on 2007-06-04
All disks are now sd*.

Concering UUID's,

apropos UUID

lists a few tools that allow to work with/manipulate UUIDS.

---

### Post by tommcd on 2007-06-04
I think these UUIDs cause as many problems as they potentially solve. Example: after a clean install of zenwalk 4.6 on my /dev/sda5 ubuntu booted with errors because it could not find zenwalk by it's UUID. I suppose I could have tried blkid, but I just commented out the UUID for zenwalk in ubuntu's fstab and set zenwalk's fstab entry back the old way and all is fine. Also, my grub menu.lst does not even use a UUID for zenwalk's boot info.
How many distros are using UUID's besides ubuntu? I know zenwalk doesn't use it, nor does slackware.

---

### Post by jerremy-tamlin on 2007-06-04
Thank you so so much!

That's the information I needed what was /dev/hda* is now /dev/sda*

Cheers! :p

---

