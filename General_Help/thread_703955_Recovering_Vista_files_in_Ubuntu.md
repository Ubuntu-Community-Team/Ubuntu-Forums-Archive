---
title: "Recovering Vista files in Ubuntu"
date: 2008-02-21
forum: General Help
---

### Post by AdrianStrays on 2008-02-21
Alright here is the story.  We run Vista, and I've been contemplating switching to Ubuntu.  I downloaded a copy of Ubuntu, but it on a CD.  The next day my brother some how managed to crash the computer.  The Vista problem isn't relevant (atleast in my eyes) but if you care to take a look for more backstory here is the link: 

[http://vistaforums.com/Forum/Topic14717-9-1.aspx](http://vistaforums.com/Forum/Topic14717-9-1.aspx)

Any whoo, the plan I formulated was as follows: Use the Ubuntu disk, run Ubuntu Live, find a way to rescue important files.  I attempted to mount the drive and received the following message: 

Alright, I attempted to mount the drive and this is what I got:

"$Logfile indicates unclean shutdown (0,1) Failed to mount '/dev/sda1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sda1/media/HP -o force Or Add the option to the relevant row in the /ect/fstab file: /dev/sda1/media/HP ntfs-3g defaults, force 0 0"

I attempted to enter the command, but it didn't work.  I don't know enough about Linux to even begin tackling this problem, and I could really use some help.  I am, specifically, only attempting to recover certain files, the rest of the data can go and I'll survive, but I NEED this project rescued. Any help for the noob would be appreciated....

---

### Post by taurus on 2008-02-21
What happens when you run these from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda1 /media/windows -o force
ls -la /media/windows
```

---

### Post by oilchangeguy on 2008-02-21
if this is a desktop, just remove the hard drive. jumper it to slave, and add it to another desktop, and you should be able to get your data.

---

### Post by Roryking on 2008-02-22
> **taurus said:**
> What happens when you run these from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda1 /media/windows -o force
ls -la /media/windows
```

Before using the "force" command, I would "sudo ntfsfix" the partition. It's a very simple fixer (compared to chkdsk), but it might save you some heartache. Install ntfsfix by installing ntfsprogs.

My method:
```
sudo apt-get update
sudo apt-get install ntfs-3g ntfsprogs
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda1 /media/windows -o force,ro
ls -la /media/windows

```

Please note I also marked the partition to mount "read-only" Drop off the "ro" part on the mount command if you feel this is unnecessary.

---

