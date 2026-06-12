---
title: "Kde partition manager and encrypted usb flash drive"
date: 2024-01-27
forum: General Help
---

### Post by ckrles on 2024-01-27
HI! At home I use Ubuntu 22.04 Lts. I encrypted a usb flash drive with Luks. In my job we use an Ubuntu-based distro with KDE neon plasma. When I plug the usb encrypted drive in a pc in my job I get a popup prompt requiring the password. I type it in, but it fails. I get a prompt requiring the kdewallet password (I think there is no password). After trying several times, it seems like the system is accessing and decrypting it, but it gets stuck trying.


I have also tried to install KDE Partition Manager in my Ubuntu in order to format and encrypt the usb drive, but KDE Partition Manager does not show the Luks encryption option which I do see in some tutorials.

Any ideas to have an encrypted and usb flash drive working on both OS's?

In my job there are many computer. One day I use a computer, and another day a different one. So, it's not a problem of a specific unit.

Thank you very much.

---

### Post by #&amp;thj^% on 2024-01-27
If I read correctly this " I get a prompt requiring the kdewallet password (I think there is no password)" That would be the the Admin password for that PC. Do you know that password?

---

### Post by yancek on 2024-01-27
If you created your encrypted usb on Ubuntu, where is the passphrase stored that you need to access/decrypt?  Probably on Ubuntu so the passphrase you are being asked for on Neon is probably not know if it stored somewhere on Ubuntu.  I dont' do encryption so I would think you need to do a little research to find where the encrypted passphrase is stored.  If it is in some location on your Ubuntu system that won't help.  If it stored somewhere on the usb, it should be accessible.

I don't know why you are trying to use the KDE partition manager or what it has to do with your problem.  You already encrypted the drive, right?  So you want to decrypt on another machine and that machine would need to know the passphrase.  I did a quick online search but didn't find anything useful and don't expect to continue looking.  Good luck.

---

### Post by #&amp;thj^% on 2024-01-27
I suspect the OP used a root method on his partition, see screenshot 1st.

I need to know if that's the case if so my first reply is valid, if you chose Everyone then you have no issues unlocking your encrypted drive:
```
df -hT /media/me/locked/
Filesystem                                            Type   Size  Used Avail Use% Mounted on
/dev/mapper/luks-128b568c-5c79-47c1-9906-b1fee4f01a83 btrfs   15G   40M   15G   1% /media/me/locked

```
mine has gone form PC to PC all linux OS's I have no problems unlocking mine.
```
cd /media/me/locked/ && ls
total 0
drwxr-xr-x 1 me me 3.1K Jan 27 13:43 Documents
drwxr-xr-x 1 me me    0 Jan 25 15:58 Music

```

---

### Post by ckrles on 2024-01-28
> **1fallen said:**
> If I read correctly this " I get a prompt requiring the kdewallet password (I think there is no password)" That would be the the Admin password for that PC. Do you know that password?

I have tried the admin password of the system in my job with no success on more than one computer.

> **yancek said:**
> If you created your encrypted usb on Ubuntu, where is the passphrase stored that you need to access/decrypt?  Probably on Ubuntu so the passphrase you are being asked for on Neon is probably not know if it stored somewhere on Ubuntu.  I dont' do encryption so I would think you need to do a little research to find where the encrypted passphrase is stored.  If it is in some location on your Ubuntu system that won't help.  If it stored somewhere on the usb, it should be accessible.

I don't know why you are trying to use the KDE partition manager or what it has to do with your problem.  You already encrypted the drive, right?  So you want to decrypt on another machine and that machine would need to know the passphrase.  I did a quick online search but didn't find anything useful and don't expect to continue looking.  Good luck.

I encrypted my usb drive with Disks and the Luks option and on my Ubuntu pc. 
As for KDE Partition Manager, I installed it on my Ubuntu pc in order to use it to encrypt my usb drive. Just in case it had something to do. Curiously, no option to encrypt appears when I use KDE Partition Manager on Ubuntu.
> **1fallen said:**
> I suspect the OP used a root method on his partition, see screenshot 1st.

I need to know if that's the case if so my first reply is valid, if you chose Everyone then you have no issues unlocking your encrypted drive:
```
df -hT /media/me/locked/
Filesystem                                            Type   Size  Used Avail Use% Mounted on
/dev/mapper/luks-128b568c-5c79-47c1-9906-b1fee4f01a83 btrfs   15G   40M   15G   1% /media/me/locked

```
mine has gone form PC to PC all linux OS's I have no problems unlocking mine.
```
cd /media/me/locked/ && ls
total 0
drwxr-xr-x 1 me me 3.1K Jan 27 13:43 Documents
drwxr-xr-x 1 me me    0 Jan 25 15:58 Music

```

Nothing out of the ordinaryt. I haven't used any root option. I simply opened Disks in my Ubuntu Pc and formated the usb drive with the Luks option. Then, in my job computer(s), I plug it in I'm required to type in the usb drive password, but the system then requires the kdewallet password. Then nor my uder password nor the admin password work. After retyping the passwords a few time it gets stuck in decryting.
I wondered if it is come kind of bug or if I am doing something wrong.

At home I have another pc, a laptop, where no issues appear when decrypting. That's why I suspect it has something to do with KDE Neon/Plasma.

---

### Post by #&amp;thj^% on 2024-01-28
> **ckrles said:**
> 

At home I have another pc, a laptop, where no issues appear when decrypting. That's why I suspect it has something to do with KDE Neon/Plasma.

Sounds Like a reasonable guess, I've not used Neon so I'm no help in confirming or denying that.

You may have to check with your IT department on that. (The KDE Wallet is the Admin password make sure you have the needed permissions)
Good Luck

---

