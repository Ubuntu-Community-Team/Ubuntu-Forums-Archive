---
title: "Every Thumb Drive owned by ROOT"
date: 2020-02-01
forum: General Help
---

### Post by saywot on 2020-02-01
Here's a thing that's puzzled me for about a week now
 Every USB drive I connect to my PC is owned by root.
Once all I had to do was run chown in a terminal and that would bring things back to normal. Now every time and on every drive I get 
chown: changing ownership of 'all-USB-Drives': Operation not permitted
doesn't matter that I run it as SUDO 
I tried changing permissions on the drive to 777 but I cannot change the ownership of the drive(s)
They're OK in other computers, just not in this Ubuntu 19.04
(I want to delete a few backups, on this drive before I upgrade but 19.04 stays until I can take ownership of at least one USB drive

---

### Post by guiverc on 2020-02-01
Ubuntu/Lubuntu 19.04 (or all 19.04 releases) are now EOL so I'd suggest release-upgrading to 19.10 asap.

[http://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/](http://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/)

Use a LTS or l*ong-term-support* release if you don't like *release-upgrading* every 6-9 months.

---

### Post by Impavidus on 2020-02-01
What filesystem is on those usb drives? Most use fat, exfat or ntfs for Windows compatibility and those filesystems don't support Unix permissions. Also, how do you mount your usb drives? Using default settings and a fat32 usb drive it should mount automatically at /media/your_username/some_label/ and be owned by you.

---

### Post by saywot on 2020-02-01
I'm trying to take a back-up of essential data via USB but can't take ownership of any external drive.

---

### Post by saywot on 2020-02-01
> **Impavidus said:**
> What filesystem is on those usb drives? Most use fat, exfat or ntfs for Windows compatibility and those filesystems don't support Unix permissions. Also, how do you mount your usb drives? Using default settings and a fat32 usb drive it should mount automatically at /media/your_username/some_label/ and be owned by you.
I'm not to sure how to describe how I mount a Usb drive but ..
1. purchase USB drive
2. insert it into a dedicated USB slot
3. the drive auto-mounts and is visible in Nautilus
4. it is mounted at /media/my_Name
5. it is owned by root and I can't change properties because I'm not the owner

the drive is as-purchased and is formatted as FAT32

no amount of CHMOD or CHOWN gives me any control over the drive because as I've said the terminal returns an "operation not permitted" message

---

### Post by saywot on 2020-02-02
> **guiverc said:**
> Ubuntu/Lubuntu 19.04 (or all 19.04 releases) are now EOL so I'd suggest release-upgrading to 19.10 asap.

[http://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/](http://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/)

Use a LTS or l*ong-term-support* release if you don't like *release-upgrading* every 6-9 months.

How does this help me to write files to a USB drive ?
I'm sort of stuck now, I won't risk data loss by upgrading without a verified back up to a few devices
But you're suggesting (I think) that the only way to gain access to an external drive is to upgrade - is that it ?

---

### Post by Impavidus on 2020-02-02
It should work the way you described it (mostly; it shouldn't mount at /media/username but at /media/username/partitionlabel or something like that). Something must be wrong with the way your drive is mounted automatically – which for me would be enough reason not to upgrade to 19.10, but to make it a fresh install.

After you inserted the usb drive and allowed it to mount, have a look at the mount options:```
mount | grep /media
```

---

### Post by The Cog on 2020-02-02
IO agree that something is wrong. For me (aind I think it has been this way for a long time), when I insert the drive it does not mount until I click the icon that appears. Then it mounts **under** my username, e.g. I just mounted one and it appeared as /media/steve/F4A2-5FD7. root owns /media/steve, but steve owns /media/steve/F4A2-5FD7. I tried chowning /media/steve and was successful. I gave it back to root straight away. 

But this confirms what Impavidus says : I don't know what is wrong with your system and would not know how to correct it. In your position, I would "sudo -i" to become root and then back up things that needed backing up. Then do a clean install of a later version. Incidentally, I always keep /home on a separate partition so I can install the system without reformatting all my data.

---

### Post by ajgreeny on 2020-02-02
> **The Cog said:**
> IO agree that something is wrong. For me (aind I think it has been this way for a long time), when I insert the drive it does not mount until I click the icon that appears. 
<snip>
That is incorrect as well!
When you insert a USB external drive the default action is normally for it to mount automatically at [B][I]/media/username/label
[/I][/B] so I am surprised you say that external disks do not mount until you click the icon.
Have you made any system file edits that might affect this automount behaviour?

---

### Post by The Cog on 2020-02-03
> **ajgreeny said:**
> That is incorrect as well!
Oh no it isn't!
For me, it's been that way for a long time.
It is possible that I changed a desktop setting to stop automount some time in the past.
But anyway, the default mount path is the important thing here. It mounts under /media/username, not at /media/username.

---

### Post by ajgreeny on 2020-02-03
> **The Cog said:**
> Oh no it isn't!
For me, it's been that way for a long time.
It is possible that I changed a desktop setting to stop automount some time in the past.
But anyway, the default mount path is the important thing here. It mounts under /media/username, not at /media/username.
A sudden thought; is the USB disk that does not mount automatically always inserted at boot time?  

That is the only time that a USB disk does not automount in my system but if I remove it and re-attach it the mount will occur automatically.  If it's always attached it will have to be given a line in /etc/fstab to mount it at boot.

---

### Post by The Cog on 2020-02-04
No. I don't insert disks at boot time. I am guessing (haven't tried) that if they automounted, they wouldn't know which user to mount for. 
I do remember (a long time ago) that I found automounting irritating when inserting a disk with multiple partitions. So I am happy to accept that automount is the default and I switched it off. It's an option in Xubuntu settings UI somewhere, under "behaviour" I think. Can't look right now. I keep my home when installing a new release so the setting may have persisted for years.

---

### Post by ajgreeny on 2020-02-04
So we're both correct, I think.

The default must be to automount a USB drive as I've never changes that, but it can be turned off as you say, shown in my screenshot, got to from thunar->Edit->Preferences->Advanced->Volume Management.

I assume this can also be configured in other DE's and file-managers but I've been using Xubuntu now for too many years to bother with anything else.

---

