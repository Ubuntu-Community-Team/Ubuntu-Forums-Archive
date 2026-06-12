---
title: "Need help to recover personal folder"
date: 2022-05-11
forum: General Help
---

### Post by s19sg on 2022-05-11
HI all,

Recently my laptop with Ubuntu stopped working. I am not sure if i was a power supply issue or power supply, anyway it will not work anymore.

Fortunately i could extract the SSD and mount it in an external case. Connecting this to another laptop with Ubuntu i can see the file system, but not the content of my personal folder, as it is encrypted.

Anybody have any idea about how can be accessed the content of my encrypted personal folder in this conditions?

Tanks in advance

---

### Post by Rex Bouwense on 2022-05-11
What was used to encrypt your folder and do you have the passphrase?

---

### Post by s19sg on 2022-05-12
The default encryption offered at Ubuntu installation. 
Would be valid my Ubuntu user password to recover it?

---

### Post by oldfred on 2022-05-12
To get Ubuntu to see different encrypted install:
sudo apt-get update && sudo apt-get install lvm2 cryptsetup

[http://www.linuxwave.info/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html](http://www.linuxwave.info/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html)
chroot & troubleshooting Full system encryption
[https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting](https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting)

Recover files on encrypted drive
[https://ubuntuforums.org/showthread.php?t=2382995](https://ubuntuforums.org/showthread.php?t=2382995) & 
[https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line](https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line)

---

### Post by s19sg on 2022-05-16
Hi, thanks for all.

I am still strugling with this. I am not being able to mount the disk. I think it could be because the SSD is in a external case and I am connecting it through USB.

Running fdisk it not appears as /deb/sdXY

If I try to run sudo cryptsetup luksOpen /media/MY_DEVICE_PATH my_encrypted_volume I obtain a message saying "Device not compatible".

I am confused and surely missing something.

---

