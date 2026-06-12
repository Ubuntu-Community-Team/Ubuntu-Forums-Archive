---
title: "Change permissions of a new partition(ext4)?"
date: 2013-03-20
forum: General Help
---

### Post by hootis on 2013-03-20
Basically I've created a new partition in Gparted however it is root access only and there is no easy way(GUI) to change the permission.
There was a thread on here, that I found a through google has a terminal command to fix the problem however, I don't understand how to edit the cmd to fit my system.

Heres the link [http://ubuntuforums.org/showthread.php?t=1137537](http://ubuntuforums.org/showthread.php?t=1137537)

-"sudo chown -R username:username /partition/mountpoint"
Heres What I though would work
username = hootis
mount = /media
partition /dev/sdc5 (it is an extended logical partiton if that make a difference)
sudo chwon -R hootis:hootis /dev/sdc5/media but it says that that location dose not exist

---

### Post by tgalati4 on 2013-03-20
```
cd /media
sudo mkdir temporarydirectorythatIwilldeletelater
sudo mount /dev/sdc5 temporarydirectorythatIwilldeletelater
sudo chown -R hootis:hootis /media/temporarydirectorythatIwilldeletelater
sudo umount temporarydirectorythatIwilldeletelater
sudo rmdir temporarydirectorythatIwilldeletelater
```

Now go into Nautilus "Places" and you should see a disk.  Double click it and it should mount and display your files.

---

### Post by Bashing-om on 2013-03-20
hootis; Hi !

Permissions are changed at the file system level, not on the devices (sdc5 = extended partition as a device);
You want to change the permissions on the directories that are contained in logical partitions contained in that extended partition.

To help us help you, post the output of terminal code:
```
sudo fdisk -lu
```

See tgalati4's last post.[INDENT=3]further advise pending
[/INDENT]

---

### Post by hootis on 2013-03-20
That seems like it did the trick, Thanks A Bunch

---

