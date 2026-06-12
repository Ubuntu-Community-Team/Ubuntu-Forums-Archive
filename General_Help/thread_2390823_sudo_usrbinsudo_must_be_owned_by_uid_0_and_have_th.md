---
title: "sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set"
date: 2018-05-02
forum: General Help
---

### Post by wil.co on 2018-05-02
Hi,

I moved my ubuntu installation from my HDD to my SSD, but now my permissions seem to be messed up.. For example; i can't run my installed Chrome browser anymore, and running sudo gives me the **sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set** error.

I've used this manual to move my installation to my SSD; [https://askubuntu.com/a/40454](https://askubuntu.com/a/40454)

Any idea what's going wrong?

I've also already tried to reboot in recovery mode and chown / chmod the /user/bin/sudo file / directory as root..

---

### Post by Impavidus on 2018-05-03
If the permissions or ownership of sudo is the only thing that's wrong, then you can fix it from recovery mode. Boot into recovery mode, remount the file system in read-write mode and fix it:```
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
```
However, the command you used to copy the file system from one drive to another doesn't refer specifically to /usr/bin/sudo, so I expect permissions or ownership will be messed up all over the place. The broken web browser also suggests more's going on. So if the install on the HDD is still intact, I suggest you wipe the SSD and try again. I would use rsync instead of cp, although, as commenters in your link say, it should work with cp.```
sudo rsync -aXS /path/to/hdd /path/to/ssd
```Then fix fstab and grub. The answer in your link assumes you have an old-fashioned bios/mbr system. If you have a newer uefi system, fixing grub will be a little different. But that was not your problem.

If you already wiped that HDD, just reinstall.

---

