---
title: "Grub2 broken after upgrade : always bring me to &quot;minimal bash like&quot; prompt"
date: 2015-02-13
forum: General Help
---

### Post by vinz92 on 2015-02-13
Hi All,

After an upgrade, my grub2 seems broken, I always arrive to the "minimal bash like" prompt of grub, and I need to manually enter the "linux", "initrd", and "boot" command to start my OS.

So when the OS is started, I tried to fix this by reinstalling grub and update it, but it change nothing!! I don't know what to do to fix this....

To explain my setup:

2 disk with each:

1 little partition (sda1 : /boot, and sdb1 : a copie of /boot, in case the first disk die)
1 swap partition in raid1: md0
1 / partition in raid1 : md1
1 /home partition in raid1 : md2

my goal is to fix the grub on sda.

I tried the classic commands:

```

root@ub > grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.
[16:07:08] - [~]                                                                                                                                                                                        [13-02-2015]
root@ub> update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done


```

with no pb... I tried too:

```

apt-get install --reinstall grub-pc grub-common

```

but same thing....I don't know what to do more....

If you have any clue...

thx a lot in advance

---

### Post by sgage on 2015-02-13
Have you tried working from a LiveCD-type session and chrooting into /dev/sda1? Then do the update-grub, and it should be good to go.

---

### Post by vinz92 on 2015-02-13
Hi,

i was thinking that if I can boot my OS, there is no need to chroot it. But I can try (if it work with the livecd but not from the running OS, how can we explain this?)

Thx

---

### Post by cl-netbox on 2015-02-13
maybe this can help :

[http://ubuntuforums.org/showthread.php?t=2264560](http://ubuntuforums.org/showthread.php?t=2264560)

---

### Post by oldfred on 2015-02-13
If you can boot, you should not need the chroot.

Is the /boot outside the RAID? or just a standard partition?

I might run Boot-Repair and post the link to the summary report just to see what is where.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by sgage on 2015-02-13
> **oldfred said:**
> If you can boot, you should not need the chroot.

Is the /boot outside the RAID? or just a standard partition?

I might run Boot-Repair and post the link to the summary report just to see what is where.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Yes, if you are booting into your actual system, there is no need to chroot. I wasn't clear if you were or not...

---

### Post by Gvarelov on 2015-02-14
By minimal bash- like prompt you mean grub prompt? If so, at the prompt, issue:
```
set
```
and note the values of "root" and "prefix". Manually enter those values again, this time "set prefix=" and "set root=":
```
set prefix=the_value_you_took_note_of
set root=the_value_you_took_note_of
```
And then, insert the normal module and execute the normal command, since GRUB isn't executing it:
```
insmod normal
normal
```
After that update you did, GRUB is unable to locate the prefix which location is used to store the normal module and the normal executable.
If this works, it's just a temporary fix. I see you already got GRUB in the MBR. Try running update-grub to see if GRUB can straighten up its list of needed locations.

---

