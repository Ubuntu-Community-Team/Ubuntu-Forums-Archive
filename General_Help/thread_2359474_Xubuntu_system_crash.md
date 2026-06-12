---
title: "Xubuntu system crash"
date: 2017-04-24
forum: General Help
---

### Post by makem2 on 2017-04-24
When I boot xubuntu I receive a message, " Press CTRL+C to cancel system checks" or something similar. If I do nothing and wait I get:
/dev/sda2:recovering journal
/dev/sda2: clean, xxxxxxxxxxxxxxxxxxxfiles, xxxxxxxxxxxxxx blocks
Welcome to emergency mode: After logging in type "journalctl -xb" to view system logs, "Systemctl reboot, "Systemctl default" or CTRL D to try again to boot into default mode.
Give root password for maintenance(or press CTRL D to continue):
Giving root password takes me to root command prompt but I have no idea where to go from there..

I can get back to the nomal grub choices menu for advanced by "sudo reboot now" but everything seems to take me back to square one.

I have a redundant instance of xubuntu and windows 10  on the same machine and can access both from grub. I also have a bootable sdd of xubuntu.

Can anyone assist please?

---

### Post by makem2 on 2017-04-24
Found the reason for the problem:

An external SSD, set to mount on boot was not attached :-(

So the fix is to do something about 'nofail' I read some while ago to put in fstab.

At least I got my OS back :-)

Stupid, stupid, I said it first!

EDIT: UUID=xxxxxxxxxxxxxx /media/makem/256ssd ext4 nofail,noatime,defaults 0 2

worked for me.

---

