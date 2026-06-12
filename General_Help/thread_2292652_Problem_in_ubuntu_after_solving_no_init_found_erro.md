---
title: "Problem in ubuntu after solving no init found error"
date: 2015-08-30
forum: General Help
---

### Post by himanshu3110 on 2015-08-30
Hi admin,
I have problem in booting ubuntu after installing some updates.
It was giving me ' No init found error'. I googled it found an solution to it. 
What i did was :
1. I used live ubuntu usb disk and click on 'try ubuntu without install' option.
2. sudo fdisk -l
3. sudo fsck -y /dev/sda6
4. sudo fsck -y /dev/sda9



This resolved my error. Then i tried booting my ubuntu. It shows me some logs like before when there was 'no init error' but there was no *initramfs *error this time.I log into my ubuntu account. But there are lot of bugs now.

I am not able to see most of icons.When i click on **Files** I got below image. Clearly, there is something wrong with icons.

Also I am not getting any sound increase/decrease onscreen  notifications, brightness notifications when i tried to change by using  fn + arrow keys, Internet connectivity icon etc.
Please help.

---

### Post by himanshu3110 on 2015-08-30
PFAs.

---

### Post by himanshu3110 on 2015-09-01
please help.

---

### Post by v3.xx on 2015-09-01
Try to clean it up.  If you get any errors, please post.

```
sudo dpkg --configure -a

sudo apt-get -f install
```

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by dino99 on 2015-09-01
is it ubuntu, and which ? or some other flavour ?
is it a fresh install or one with many dist-upgradings ?
do you have installed 'extra' 'untrusted' (non genuine ubuntu packages) ?
do you run some commands to clean the system ? (clean/autoclean/autoremove/....)

---

### Post by himanshu3110 on 2015-09-05
himanshu@himanshu-Ideapad-Z570:~$ sudo dpkg --configure -a
**dpkg: error: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory**

Also, I got the same 'no init found error' while starting ubuntu. I run fsck commands again using live usb disk.

---

### Post by himanshu3110 on 2015-09-05
yes, ubuntu 14.04. 
I did install some regular updates and after that this problem happens.

---

### Post by v3.xx on 2015-09-05
> dpkg: error: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory

I wonder what happen to it.  Try this ..

```
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status

```
Follow with ..

```
sudo apt-get update
```

If that much goes without any errors ..

```
sudo apt-get dist-upgrade
```

---

