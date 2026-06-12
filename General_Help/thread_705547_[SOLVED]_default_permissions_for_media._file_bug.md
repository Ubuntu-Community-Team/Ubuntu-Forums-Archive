---
title: "[SOLVED] default permissions for media. file bug?"
date: 2008-02-23
forum: General Help
---

### Post by Arand on 2008-02-23
Hi, I would like to report a problem, but I am not sure about the procedure, and if this is a 'bug' or more an 'idea', and since it affects both gutsy and hardy-alpha5, should I do two reports?

This is what I would like to report:

> I think that NTFS media should be mounted as read-only (for non-root users) by default.

After installing Ubuntu I have full read-write access to both my NTFS partitions, without being root. Since one of these is the partition where my first OS is installed (windows), it seems very bad to give the common user full -rw.

Looking in my /etc/fstab I see that these partitions indeed has umask of [007] set, (I can set them to 027, and it works as I want).

This to me seems to be a rather severe security issue...

Can I just put this text down with a note of 'aplies to gutsy&hardy-a5' as a bug report in launchpad?

Also, the livecd for hardy-a5 seems to actually do this rather nicely, if I remember correct. So that the media is unmounted at start and has to be unlocked with password to be accessed. Anybody knows if this is how hardy is supposed to work in final?

I think the best solution would be if the 'permissions' tab for media properties could be unlocked via the new authorization tool, would it be to late to give such a feature suggestion? And again, how would I file such a suggestion?

-Arand

---

### Post by mikewhatever on 2008-02-24
How would the system know if that's the Windows partition or just another one for storage? I think a better solution would be disabling the mounting off certain partitions, so that they do not show anywhere. At the moment, if you do not mount ntfs partitions during the installation, they show up as unmounted in Nautilus and can be mounted with root password, sort of the way you want it. Strangely enough, it can be done with a FAT32 partitions. Now, umask=007 may seem like a wrong value, but if the user and group are root, then all non root users get zero permissions. In my case, it says gid=46 in ntfs fstab line, which is an obscure group.

---

### Post by Arand on 2008-02-24
**EDIT:** Wrong there, the default user** is** part of the plugdev group... Explains that. Buth now I'm a bit confused, should I even use this account? This is an admin account, and is it safe to use this as default acount, or is this the linux equivalence of selling my soul?** :ENDEDIT**

Yes, certainly, I meant that all NTFS partitions (and all others for that matter) should be at least non-write by default.

Thing is, I know that I have not mounted these partitions (hda1 & hda5) during install. And yet my fstab reads like this at first boot:
(the default login uid is 1000, and it is not part of 46 (plugdev), as far as I can see (using id command)) **EDIT: -Turned out to be wrong :ENDEDIT**

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=61fee76f-16e0-480a-b8a9-6e40ce024789 /               ext3    errors=remount-ro 0       1
# /dev/hda1
UUID=42901B26901B2049 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=CE5CCBFA5CCBDB7B /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda7
UUID=3f66a536-8551-4f3f-bf9d-1151b41060f1 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

This shouldn't be, right?

- Arand

---

### Post by pointone on 2008-02-24
It's the root account that deflowers your soul; the admin group in Ubuntu just means you have sudo access, which is the safer way to work.

I think the current system works fine. If you don't want people to access your other partitions, simply take them out of the plugdev group or change the umask; what's hard about that? Frankly, I want access to my other partitions more often than I want to deny access.

The Ubuntu installer adds lines in your fstab for other partitions. If you don't want them mounted at boot, just add the "noauto" option to the list of options.

---

### Post by Arand on 2008-02-24
Alright (good to know Xunil ain't got my soul yet).

My main concern was that this would be a fairly easy way for malware to access other operating systems from within Ubuntu, right?

Probably not such a big concern at the present, with very few malwares using linux/ubuntu out there. But it is still a safety issue, innit? Especially as more and more 'home-users' get into Ubuntu.

The direct -rw access does mean that for example an archive configured in the 'right' way, could, without root privileges, shove whatever stuff it sees fit onto my (in this case) windows partition?
Isn't this kind of a virusmakers dream?

I am fairly new to linux, but is this fully possible?

- Arand

---

### Post by mikewhatever on 2008-02-25
I see your point, but default settings are usually a fragile balance between usability and convenience, versus security and restriction. Should there be no write access to NTFS by default, lots of users would have to manually modify fstab lines for their NTFS storage partitions. I don't know what's better. Has there been any indication of malware using Linux to infect Windows?

---

### Post by Arand on 2008-02-25
Frankly I have no idea if this has happened, or is likely to happen, it's just a thing that struck me really. And if the alternative would be to edit fstab to GET the write access I do see the point of leaving it like this.

But one should perhaps put down an idea for Ibex, so that media can be non-write (and maybe non-read also) by default, and then have an easy way to change these permissions, upon first access of the media.

I'm going to put an [EXPLAINED] tag on this thread, since it's kinda-solved (and as of now cannot be 'solved' 'properly', so to speak...)

EDIT: Ach, 'solved' is the only tag available, so be it. :ENDEDIT

- Arand

---

