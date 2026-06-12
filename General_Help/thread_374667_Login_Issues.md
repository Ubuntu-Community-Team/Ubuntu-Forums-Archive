---
title: "Login Issues"
date: 2007-03-02
forum: General Help
---

### Post by stern_matt on 2007-03-02
Just installed Edgy on a PIII Dell with 128 Mb of RAM.  When I login, the desktop begins to load but then I am booted back out to login screen.  If it matters, I did an OEM install and I am logging in with "OEM" username.

Just ran df -h, here are the results:

/dev/hda 13G 1.8G 9.9G 16% /
varrun 62M 12K 62M 1% /var/run
varlock 62M 0 62M 0% /var/lock
procbususb 10M 140K 9.9M 2% /proc/bus/usb
udev 10M 140K 9.9M 2% /dev
devshm 62M 0 62M 0% /dev/shm

Any help is greatly appreciated.

---

### Post by taurus on 2007-03-02
The first line of your output looks a little strange!

```
**/dev/hda** 13G 1.8G 9.9G 16% /
```
See if you can boot into recovery mode from GRUB menu and paste the output of this command here.

```
fdisk -l
```

---

### Post by stern_matt on 2007-03-02
Result of of fdisk -l

/dev/hda1 * 1 1617 12988521 83 Linux
/dev/hda2   1618 1662 361462+ 5 Extended
/dev/hda5 1618 1662 361431 82 Linux swap / Solaris

---

### Post by taurus on 2007-03-02
What about

```
cat /etc/fstab
```

---

### Post by stern_matt on 2007-03-02
# /etc/fstab: static file system information
#

proc /proc proc defaults 0 0
UUID-477955fa-9228-4e05-9ff9-505043486db7 / ext3 defaults, error
s=remount-ro 0
UUID=eefc0648-aab6-4ae6-a795-4211fe2d2719 none swap sw
0  0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw, user,noauto 0 0

---

### Post by taurus on 2007-03-02
Edit /etc/fstab

```
nano -Bw /etc/fstab
```
and change this line

```

UUID-477955fa-9228-4e05-9ff9-505043486db7 / ext3 defaults, errors=remount-ro 0

```
to look like this.

```
/dev/hda1   /   ext3   defaults,errors=remount-ro    0   1
```
Save it and exit with <Ctrl>o and <Ctrl>x.

Reboot and see if you can log in with username **oem** and your password.  After log in, don't forget to run this command to create an actual account so you can use it from then on.

```
sudo oem-config-prepare
```

---

### Post by stern_matt on 2007-03-03
Making progress...

I can now log into the system...sometimes.

Will log in and get bumped out as before.  Sometimes it will display this following error:

"I've detected a panel already runnin, and will now exit."

Other times it will freeze with just the desktop wallpaper showing.

However, once after getting bumped out a few times, I was able to log in.

UPDATE

Was able to log in again.  Was bumped out once, logged in again, received error message, then the everything loaded properly.

---

