---
title: "Sharing and drive mounting wierdness"
date: 2012-12-16
forum: General Help
---

### Post by Bendezium on 2012-12-16
Nearly a total noob here trying to setup Ubuntu 12.10 as a home fileserver. I have two IDE drives. One I use for Media, with a 10 GB partition for Ubuntu, the other I use as a Backup Drive. I'd like to share both of these so I can access them from my Windoes 8 machine and Android devices.

Every time I select properties of a drive, and enable sharing, Nautilus installs some permissions, however when I go right back into properties the Sharing box is no longer checked. I can see the drives from my phone but can't access them. A few times this worked temporarily but I did not seem to do anything different.

/mnt is empty, and from my understanding is where permanent drives should mount.

/media is setup like this, which seems rather odd and I don't know how it got this way:
/media/BackupDive - Owner is root, contents are unreadable
/media/MediaDrive - Owner is root, contents are unreadable
     /media/Bendezium/BackupDrive - Takes me to the mounted IDE Backup Drive
/media/Bendezium/MediaDrive1 - Takes me to the mounted IDE Media Drive

I feel like the screwed up /media folder is a result of the tampering I've been doing to try to fix sharing. Anybody have any ideas on how to straighten this all out? Thanks!

---

### Post by Mopar1973Man on 2012-12-16
Ok... I'll try and help the best I can.

If you want permanent mounted drives then you might want to read up on Fstab or you can install pysdm.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

```
sudo apt-get install pysdm
```

So now that deals with the mounting issues. 

As for file sharing you can get more info here... (Samba)
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by Bendezium on 2012-12-28
Thanks for trying to help. I wish I could have gotten this sooner but I've been busy with holidays and also setting up my primary Windows machine.

I was able to permanently mount my drives using fstab. Thanks, that was a huge accomplishment!

Samba on the other hand... not so easy. I had samba installed and updated when I posted originally last time. It very much seemed to be working intermittently. For example, I went to bed one not unable to access my shared drive, and when I woke up they were working. When I got home from work, they were again not working.

It's come to a complete stand still recently and I can never access them. I'm unable to ping the linux box from either both my android phone and windows machine.

I had a brief break through when I used sudo ufw disable. I was able to ping my linux ip and see the computer in windows network connections. I renabled ufw and then disabled again and was not able to ping.

This is so bizarre! Any ideas?

---

### Post by windscape on 2012-12-28
Hi,

Since you presumably trust the machines on your LAN, the server is not serving anything to the Internet, and you presumably have a router with its own firewall, the ufw firewall on the server is probably the root cause of your issue. I have a 12.04.1 LTS server without ufw installed or enabled and its samba sharing is rock solid to the Windows machines on my LAN. I don't access the server from the Android machines on my LAN.

---

### Post by Bendezium on 2012-12-29
> **windscape said:**
> Hi,

Since you presumably trust the machines on your LAN, the server is not serving anything to the Internet, and you presumably have a router with its own firewall, the ufw firewall on the server is probably the root cause of your issue.

A buddy of mine told me the same thing! I have ufw permanently disabled now. I've also forwarded ports 135, 137-139 and 445 in my router settings and updated my drivers on my windows machine. Windows can now see my linux box in the network but can't access it.

I'm making baby steps I guess. Currently waiting on my buddy to get back to me. I'll post more when I get any update but I've been working on this for a few hours today and need a break until I catch a lead. Always open to more feedback. Thanks!

---

