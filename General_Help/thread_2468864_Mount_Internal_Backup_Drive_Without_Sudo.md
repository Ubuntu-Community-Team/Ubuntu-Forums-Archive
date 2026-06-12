---
title: "Mount Internal Backup Drive Without Sudo"
date: 2021-11-12
forum: General Help
---

### Post by Quarkrad on 2021-11-12
I have an rdiff-backup script that works well - it backs up what I want to an internal HD (/dev/sdb1).  I run this script when I shut down the pc (stand-alone Desktop).  I'm experimenting  (to avoid ransomware corrupting my backup HD) not having my backup HD connected when I boot.  Hence I have commented out the following entry in my fstab:

```
#UUID=4a5497c8-2421-4195-93a4-42aea5724203 /media/dad/backup       ext4    defaults,noatime     0        2
```

Not sure whether this is the right way of achieving my requirement but I also added to /etc/sudoers/config:

```
dad ALL=(ALL) NOPASSWD: /usr/bin/rdiff-backup
dad ALL=(ALL) NOPASSWD: /usr/bin/mount, /usr/bin/umount
```

When I type in a terminal sudo /usr/bin/mount /dev/sdb1 or sudo usr/bin/mount /media/dad/backup I get:

```
sudo /usr/bin/mount /dev/sdb1
mount: /dev/sdb1: can't find in /etc/fstab
```

Appreciate some help on this as I'm not doing things the right way.

---

### Post by Tadaen_Sylvermane on 2021-11-12
I've been using systemd automounts for awhile now. Works great thus far.

[https://wiki.archlinux.org/title/fstab#Automount_with_systemd](https://wiki.archlinux.org/title/fstab#Automount_with_systemd)

---

### Post by Quarkrad on 2021-11-12
My existing script looks something like:

```
sudo /usr/bin/rdiff-backup foo bar
sleep 3
shutdown -h now
```

I was hoping to amend the script to something like(?):

```
sudo /usr/bin/mount (my backup HD)
sleep 3
sudo /usr/bin/rdiff-backup foo bar
sleep 3
shutdown -h now
```

If I create a systemd unit file (mount.service) with the necessary/corrent syntax will my script be something like:

```
sudo systemctl enable mount.service
sleep 3
sudo /usr/bin/rdiff-backup foo bar
shutdown -h now
```

I ask because I don't want to waste my time working out what goes in the mount.service file if my thinking is way off. Thanks

---

### Post by Quarkrad on 2021-11-12
I guess the sudo infront of systemctl enable mount.service is going to cause me an issue re I do not want to have to enter a password

---

### Post by Quarkrad on 2021-11-12
If this method is right I believe **enable** is wrong - it should be **start** in the line sudo systemctl enable mount.service

---

### Post by TheFu on 2021-11-12
I tested systemd-automounts and discovered they mounted on demand, but didn't umount when that need ended.  Has that changed in the last year?
OTOH, autofs mounts and umounts storage as needed.

Anyway, there is at least 1 thread here with commands for using the systemd-automount stuff. 
[Https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156](Https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156)

Until the automatic dismount works, it doesn't fit the needs for backup storage to be protected against crypto-locker-like attacks.

As for the sudoers entries, there are many ways to solve the issue.  I use a Cmnd_Alias and Cmnd_Alias_Spec to drastically limit which options and commands are allowed and I use a User_Alias for the more general answer to using a deployment userid for stuff, not my personal account.  Personal accounts are more likely to become compromised, right?

---

### Post by Tadaen_Sylvermane on 2021-11-12
I don't know. I do know it hasn't caused me any problems but admittedly my access to my automounts is irregular. Never thought to actively test it. Maybe I should.

---

