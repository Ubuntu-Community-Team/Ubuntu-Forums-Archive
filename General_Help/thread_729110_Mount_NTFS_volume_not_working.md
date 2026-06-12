---
title: "Mount NTFS volume not working"
date: 2008-03-19
forum: General Help
---

### Post by Kimbie on 2008-03-19
I have looked at the other NTFS problems but dont seem to fit my problem.

Had Vista, deleted the partition Vista was on, just put on HH 8.04 a6, working ok, however when I go into Places - Computer I can see my drives but when I double click i get the following messge:

Cannot mount volume
unable to mount the volume

Details:
$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/hda1/': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/hda1 /media/disk -o force or add the option to the relevant row in the /etc/fstab file: /dev/hda1 /media/disk ntfs-3g defaults,force 0 0

This are fixed drives, not USB drives, Vista was shut down correctly before an install of Ubuntu.

I need to be able to get to these volumes, to continue to use Unbuntu.

any help is appricatedd

cheers

Kimbie

---

### Post by Oldsoldier2003 on 2008-03-19
> **Kimbie said:**
> I have looked at the other NTFS problems but dont seem to fit my problem.

Had Vista, deleted the partition Vista was on, just put on HH 8.04 a6, working ok, however when I go into Places - Computer I can see my drives but when I double click i get the following messge:

Cannot mount volume
unable to mount the volume

Details:
$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/hda1/': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/hda1 /media/disk -o force or add the option to the relevant row in the /etc/fstab file: /dev/hda1 /media/disk ntfs-3g defaults,force 0 0

This are fixed drives, not USB drives, Vista was shut down correctly before an install of Ubuntu.

I need to be able to get to these volumes, to continue to use Unbuntu.

any help is appricatedd

cheers

Kimbie
change the following code to reflect your partitions and desired mount point
```
mount -t ntfs-3g /dev/sda5 /media/sda5 -o force
```

---

### Post by Kimbie on 2008-03-19
> **Oldsoldier2003 said:**
> change the following code to reflect your partitions and desired mount point
```
mount -t ntfs-3g /dev/sda5 /media/sda5 -o force
```

How and where do I do this?

Thanks

Kimbie

---

### Post by demarshall on 2008-03-19
I need the name of the file that the mount commands are in as well. I want to mount my NTFS partition as well as an ext ? partition from a previous Linux install. I think I can figure out the format of the lines once I have the name of the file.

---

### Post by demarshall on 2008-03-19
The file that mounting rules need to be added to is: /etc/fstab

I hope this helps

---

### Post by demarshall on 2008-03-19
Backup fstab before editing it

sudo cp /etc/fstab /etc/fstab_backup

and then use Nano to edit it. Nano is a text based editor.

sudo nano /etc/fstab

---

### Post by demarshall on 2008-03-19
Restart your computer after doing what was in my last message. Once Ubuntu is up again your partition should be available to you.

---

### Post by demarshall on 2008-03-19
It turns out the command that you were given is not the same format as it should be in the fstab file and I don't know exactly how it should be formatted. We need someone to give us the format of the line for fstab so that it mounts every time. Apparently if you make even a slight error, it will stop Linux from booting.

---

### Post by mattk132 on 2008-03-19
I'm pretty sure I had this problem too.  If you're dual-booting sometimes if you have a power outage ubuntu thinks windows is using the drive.  Try going into windows and restaring correctly.:guitar:

---

