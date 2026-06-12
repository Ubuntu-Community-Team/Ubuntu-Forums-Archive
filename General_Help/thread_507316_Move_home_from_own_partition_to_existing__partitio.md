---
title: "Move /home from own partition to existing / partition?"
date: 2007-07-22
forum: General Help
---

### Post by abobrien13 on 2007-07-22
I have dual hard drives in my system.  One is mounted as "/" and the other "/home" and it all works fine, but I've come across the need for Windows reinstalled for an upcoming CnC 3LAN.  Is it possible to merge the partitions without reformatting?  Also, could I move it back to the previous form later if I decided to purge Windows?  TIA, all!

---

### Post by WhimpyPeon on 2007-07-23
You should be able to boot from a live cd and mount both drives.  Create a home folder in your root drive.  Copy everything over from the home drive to the home folder of the root drive.  Be sure to preserve your file/folder permissions.

Once the files are copied over then edit your /etc/fstab file and comment out or remove the entry for the home folder drive.

You should be able to reboot into your system now homes are on the same drive as your root.

---

### Post by Mr. C. on 2007-07-23
```
mkdir /home.new
cd /home.new
(cd /home ; tar -cvf - ) | tar -xvf -
```

Remove the /home /etc/fstab entry, and reboot.

```
rmdir /home
mv /home.new /home
```

MrC

---

### Post by Gruelius on 2007-07-23
Yes and Yes,

In a live cd enviroment do the following.

```
sudo mkdir /mnt/root
sudo mkdir /mnt/oldhome
sudo mount /dev/<drive+part> /mnt/root <----- this drive is the / drive
sudo mount /dev/<drive+part> /mnt/oldhome <--- this drive is the /home/ drive1
sudo cp -rf /mnt/oldhome/* /mnt/root/home/ (or mv if you want).
```

and then go into fstab and remove the line regarding /home/

```
sudo nano /etc/fstab
```

A tip with the install process. Remove the / drive and just install XP as if no other HDD is attatched. This will prevent you from formatting your old drive and will also stop it from planting itself over grub ;).

---

