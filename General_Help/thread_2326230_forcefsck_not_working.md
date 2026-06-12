---
title: "forcefsck not working"
date: 2016-05-29
forum: General Help
---

### Post by Moses_Moore on 2016-05-29
My Ubuntu workstation believes it needs to fsck the root filesystem, but it will not.

run-parts /etc/update-motd.d/ | sudo tee /var/run/motd.dynamic
```
Welcome to Ubuntu 16.04 LTS (GNU/Linux 4.4.0-22-generic i686)

 * Documentation:  https://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

*** /dev/sda1 will be checked for errors at next reboot ***
```

tune2fs -l /dev/sda1 |grep Last

```
Last mounted on:          /
Last mount time:          Sun May 29 21:43:51 2016
Last write time:          Sun May 29 21:43:40 2016
Last checked:             Tue Oct 27 01:51:27 2015
```


touch /forcefsck ; shutdown -h now

.... but when I power on the machine again, I get a warning that running e2fsck is recommended, instead of it actually running e2fsck. The '/forcefsck' file is missing after a reboot.

```
[   15.365778] EXT4-fs (sda1): warning: checktime reached, running e2fsck is recommended
```

The files /var/log/fsck/{checkfs,checkroot} both say "(Nothing has been logged yet.)"

What else am I overlooking?  previous threads in the forum about this problem date back to 2012 and 2008, and usually advise "touch /forcefsck; reboot" or say that the problem goes away after installing some new kernel packages (new for 2012).  I'm not sure what else to do except boot from a CD-ROM and run fsck from an entirely disconnected OS.

---

### Post by Bashing-om on 2016-05-29
Moses_Moore; Hello;

Yeah, Uh Huh .. Welcome to systemd. the old /forcefsck is no longer applicable.

To check the file system now one has to add a boot parameter to grub .
```

fsck.mode=force

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by sudodus on 2016-05-30
> **Moses_Moore said:**
> ... I'm not sure what else to do except boot from a CD-ROM and run fsck from an entirely disconnected OS.

I would do that, boot from a CD-ROM [DVD or a USB] drive and run fsck from an entirely disconnected OS, which can be made from an Ubuntu iso file,

```
sudo e2fsck -cf /dev/sdxy
```

where x is the drive letter and y is the partition number (of your root partition).

---

