---
title: "GDM failure"
date: 2007-12-14
forum: General Help
---

### Post by Kindredgarou on 2007-12-14
hi guys i did some updates yesterday night including a library update and nvidia drivers (also finally got wine 9.5 working) and when i tried to login today i get a gdm error saying no group gdm. the only access i ghet is through a command line terminal and using my live disc to boot ( how i got on here) any ideas??
thanks in advance

---

### Post by taurus on 2007-12-14
Boot into recovery mode from GRUB menu and add group gdm to your /etc/group and see if that fixes the problem.

```
nano -B /etc/group
```
And add this line to the end of it.

```
gdm:x:118:
```
Save it with <Ctrl>o and exit with <Ctrl>x.  Then, reboot with

```
shutdown -r now
```

---

### Post by Kindredgarou on 2007-12-14
would love to but cant boot into recovery mode , was my first idea to try

---

### Post by taurus on 2007-12-14
In that case, boot your machine with the LiveCD and mount the partition where / is located.  _Assuming_ it's /dev/sda1, open a terminal and run

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/etc/group
```
You can unmount it before reboot if you wish.

```
sudo umount /mnt/ubuntu
```

---

