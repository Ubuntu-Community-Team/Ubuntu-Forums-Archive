---
title: "Improper reported disk usage"
date: 2014-06-29
forum: General Help
---

### Post by Brandon_MacEachern on 2014-06-29
MATE is reporting a huge amount of disk usage, which is quite impossible for my laptops 750GB HD.

Ubuntu 14.04 with MATE.

Here's a screenshot showing what I am seeing:
[https://fbcdn-sphotos-d-a.akamaihd.net/hphotos-ak-xpa1/t31.0-8/10477570_10202389971374693_6788659427894293808_o.jpg](https://fbcdn-sphotos-d-a.akamaihd.net/hphotos-ak-xpa1/t31.0-8/10477570_10202389971374693_6788659427894293808_o.jpg)

140.9TB?  If it was GB I'd believe it more, but that's quite a lot of bytes that I definitely don't have.  Unless my hard drive discovered the lottery, lol.

EDIT:  Yes, I checked the HD, nothing wrong found, and also using the disk usage analyzer, all is well.

---

### Post by ibjsb4 on 2014-06-29
How bout
```
df -ah
```
[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by Brandon_MacEachern on 2014-06-29
Right, so nothing there shows this huge disk usage.

```
brandon@BrandonsLinuxLaptop:~$ df -ahFilesystem      Size  Used Avail Use% Mounted on
/dev/sda5       559G  135G  396G  26% /
proc               0     0     0    - /proc
sysfs              0     0     0    - /sys
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none               0     0     0    - /sys/fs/fuse/connections
none               0     0     0    - /sys/kernel/debug
none               0     0     0    - /sys/kernel/security
udev            3.9G  4.0K  3.9G   1% /dev
devpts             0     0     0    - /dev/pts
tmpfs           790M  1.5M  789M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G   16M  3.9G   1% /run/shm
none            100M   32K  100M   1% /run/user
none               0     0     0    - /sys/fs/pstore
binfmt_misc        0     0     0    - /proc/sys/fs/binfmt_misc
systemd            0     0     0    - /sys/fs/cgroup/systemd
gvfsd-fuse         0     0     0    - /run/user/1000/gvfs
brandon@BrandonsLinuxLaptop:~$ 

```

I guess as far as a GUI goes, it's just a bug and I have to live with that one too?  I don't have huge TB's ammounts of data like it claims.

---

### Post by dragonfly41 on 2014-06-29
You can install **testdisk** (from Ubuntu Software Centre) and analyse your drive to look for any geometry errors in the testdisk report.

---

### Post by Brandon_MacEachern on 2014-06-29
Nothing reports any problems.

In fact, I think this could be a MATE bug with Caja, all installs are doing the same thing, reporting some oddly huge TB size.

---

### Post by Brandon_MacEachern on 2014-07-01
Problem solved, the file manager is including Kcore.  It really shouldn't.

---

