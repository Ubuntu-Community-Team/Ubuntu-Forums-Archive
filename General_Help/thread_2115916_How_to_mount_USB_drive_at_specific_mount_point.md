---
title: "How to mount USB drive at specific mount point"
date: 2013-02-14
forum: General Help
---

### Post by zerubbabel on 2013-02-14
I have a usb backup drive with an encrypted partition (LUKS) that mounts fine via the Kubuntu device notifier/manager, but it mounts at a randomly generated mount point like "/media/cfec1033-5158-4ec4-974b-b51f012ab1c4". I would like to mount it at a more useful mount point, such as "/media/backup". Is there any way to make that happen via the Kubuntu device notifier/manager gui?

---

### Post by HermanAB on 2013-02-14
If you give the device the volume label 'backup' then it will be automounted at /media/backup.

Otherwise, put an entry for it in /etc/fstab and mount it under /mnt

---

### Post by Bufeu on 2013-02-14
Mount it manually then.
[I]sudo mount /dev/<what-the-usb-may-be-called> /path/to/mounting-point
[/I]

---

### Post by zerubbabel on 2013-02-14
> **HermanAB said:**
> If you give the device the volume label 'backup' then it will be automounted at /media/backup.

Otherwise, put an entry for it in /etc/fstab and mount it under /mnt

The partition manager does not allow me to set a label. 

Back when I was running Ubuntu I used to be able to create an encrypted partition and give it a label such that it would mount at "/media/backup". I still have an older encrypted usb drive that mounts that way. But under Kubuntu I can't seem to find a way to do that. I even installed the Gnome disk utility under Kubuntu, but when I run it, it lists the devices but doesn't let me modify anything. There is absolutely nothing active in its gui. It is "display only".

I created the partition with the sequence:

sudo cryptsetup --verbose --verify-passphrase luksFormat /dev/sdd1
sudo cryptsetup luksOpen /dev/sdd1 OffSite
sudo mkfs.ext4 /dev/mapper/OffSite

But it does not mount as "OffSite" as I expected it would.

---

### Post by zerubbabel on 2013-02-14
Well, I solved my problem in a roundabout way. I installed the latest Ubuntu 13.04 nightly in a virtual box and re-created the encrypted partition using the Gnome disk utility, complete with the label "offsite", and it mounts automatically as "/media/offsite". 

I wish I knew how to make that happen in Kubuntu, as I prefer KDE to Unity.

---

### Post by zerubbabel on 2013-02-15
Now, after seeing the layout of the Gnome disk utility in 13.04, I could find its controls when installed in Kubuntu 12.10. The problem was that for some reason its button icons weren't displayed, so if you didn't already know where they were, there didn't appear to be any way to operate on the disks. But knowing where they're supposed to be, you can hover over them and the fly-over text appears. Strange.

Still, I would expect that KDE would have an equivalent tool, but I can't find one.

---

### Post by Bufeu on 2013-02-15
> **zerubbabel said:**
> Now, after seeing the layout of the Gnome disk utility in 13.04, I could find its controls when installed in Kubuntu 12.10. The problem was that for some reason its button icons weren't displayed, so if you didn't already know where they were, there didn't appear to be any way to operate on the disks. But knowing where they're supposed to be, you can hover over them and the fly-over text appears. Strange.

Still, I would expect that KDE would have an equivalent tool, but I can't find one.
KDE Partition Manager: [http://blog.volker-lanz.de/2010/05/29/new-in-kde-partition-manager-1-1-ii-smart-status-reports](http://blog.volker-lanz.de/2010/05/29/new-in-kde-partition-manager-1-1-ii-smart-status-reports)
Install it:
1. Dowload it from Sourceforge: [http://sourceforge.net/projects/partitionman/](http://sourceforge.net/projects/partitionman/)
2. via apt-get: ```
sudo apt-get install partitionmanager
```

---

### Post by zerubbabel on 2013-02-15
> **Bufeu said:**
> KDE Partition Manager: [http://blog.volker-lanz.de/2010/05/29/new-in-kde-partition-manager-1-1-ii-smart-status-reports](http://blog.volker-lanz.de/2010/05/29/new-in-kde-partition-manager-1-1-ii-smart-status-reports)
Install it:
1. Dowload it from Sourceforge: [http://sourceforge.net/projects/partitionman/](http://sourceforge.net/projects/partitionman/)
2. via apt-get: ```
sudo apt-get install partitionmanager
```

As far as I can tell, it doesn't support encryption.

---

