---
title: "Sudo doesn't work - need help fast!"
date: 2007-02-27
forum: General Help
---

### Post by Catty on 2007-02-27
Hello, I have a major problem.

I can't get the prefix *sudo* to work and since i don't have any root-user I practically can't do anything on my server. Almost the only things that works is apache & mysql.

I tried to make a tar-archive in order to make a backup on the most important things then ftp-upload it to my own comp, but the archives I make are always broken.

The error msg i get is the following:
```
:$ sudo
sudo: /etc/sudoers is mode 0666, should be 0440
sendmail: fatal: /etc/postfix/main.cf, line 104: missing atribute '=' after
 attributes: "cp /etc/aliases /etc/postfix/aliases"
```

I hope someone can help my fast, if I don't get any responses I don't know what the hell I gonna do.

Do you think the repair on the CD fix it without damaging any files on the server?


Note: I am running Ubuntu 6.06.1

---

### Post by cronholio on 2007-02-27
Boot from an Ubuntu or Knoppix (or whatever) Live CD and mount your root partition. Then  change the sudoers file's permissions (as root):

```
chmod 440 <mountpoint_of_your_root_partition>/etc/sudoers
```

---

### Post by Catty on 2007-02-27
> **cronholio said:**
> Boot from an Ubuntu or Knoppix (or whatever) Live CD and mount your root partition. Then  change the sudoers file's permissions (as root):

```
chmod 440 <mountpoint_of_your_root_partition>/etc/sudoers
```


I downloaded the latest version on Ubuntu's site (6.10) and booted up the comp with it.

But I don't know how to mount my root partition. :(

---

### Post by drpaul on 2007-02-27
It usually gets mounted during the boot of the Live CD. Depends on what kind of hard disk hardware you're running.

ATA is usually ..../hdx
SATA is usually  ..../sdx

So look for something like /media/hda1

HTH

Paul

---

### Post by madcow72 on 2007-02-27
I would ignore what I say here and check out laidback's recommended site below.  That's a great site, I'd never been there before.

[COLOR="Silver"]From the live CD, don't you have to manually mount your root partition?  Something like:
```
sudo mkdir /mnt/hda/
sudo mount -t ext3 /dev/hda1/ /mnt/hda/
```
Then you would be able to change the root permissions like was suggested above with:
```
sudo chmod 440 /mnt/hda/etc/sudoers
```[/COLOR]

---

### Post by laidback on 2007-02-27
This reference may help:
[http://psychocats.net/ubuntu/sudo](http://psychocats.net/ubuntu/sudo)

---

