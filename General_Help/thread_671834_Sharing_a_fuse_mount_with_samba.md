---
title: "Sharing a fuse mount with samba"
date: 2008-01-18
forum: General Help
---

### Post by SgtPepperKSU on 2008-01-18
This has to be a common enough combination that somebody can help me.

Here's the scenerio:

/backup is a RAID+LVM partition that is shared with samba.  It works fine and I use it to back up files from my other computers.

/backup/FLAC is where my flac music files are backed up

~/music/flac is symlinked to /backup/FLAC

~/music/mp3/96kbps, ~/music/mp3/128kbps, ~/music/mp3/160kbps, ~/music/mp3/192kbps are all mp3fs mounts to /backup/FLAC at various bitrates

I'd like to share ~/music with samba so I can access the mp3 version of songs from my other computers (windows).  However, when I share the folder all of the mounted folders in ~/music/mp3 don't show up.  If I create any other files there, they show up.  If I leave any of the folders unmounted, they show up (empty).  All of the flac files in ~/music/flac show up.  Just not the mounted folders.

I've tried mounting these folders with encfs as well, and I get the same results.  So, it seems to be FUSE mounting in general that make the folders invisible when viewed over the network.

In other posts I've seen, people have had troubles with their permissions, but I've tried having all components (/backup/FLAC files, samba share to /backup/FLAC, mp3fs mount, and samba share to ~/music/mp3/...) have *full* permissions and the problem remains.

Any ideas?

---

### Post by SgtPepperKSU on 2008-01-18
Shoot, forgot to mention that I'm running a fully-updated Kubuntu 7.10.

Also, here is the relevant section of my smb.conf:
```
[backup]
comment = RAID Backup Folder
path = /backup/keith/
valid users = keith
write list = keith
create mask = 0755
directory mask = 0755

[music]
path = /home/keith/music/
comment = Keith's Music Libary

```

---

### Post by fjgaude on 2008-01-20
Not sure if this helps but this is what the bottom of my smb.conf looks like, as set by the Ubuntu Shares GUI:
```


[frank]
path = /home/frank
available = yes
browsable = yes
public = yes
writable = yes

[raid]
path = /home/raid
available = yes
browsable = yes
public = yes
writable = yes
```

---

### Post by SgtPepperKSU on 2008-01-20
Thanks, but I just tried setting up a share with identical settings as that, and I get the exact same results.

I browse to my samba share from windows (or from the same ubuntu box via "Remote Places"), all files and folders show up at first.  Then as soon as I mount one of the folders using a FUSE filesystem, it disappears from view (from the network, it still shows up locally on the ubuntu box, of course).  I'm at a loss as to how to continue...

Surely someone else has shared a FUSE mounted folder via samba, right?

---

### Post by SgtPepperKSU on 2008-01-26
FYI: I just got it working by adding ```
-o allow_other
``` when mounting the folders.  I hadn't tried this before because I had tried to no avail ```
force_user = keith
``` in my smb.conf and thought that would be viewing the folder with the permissions of user keith, but apparently that just affects the owner of new files being created.

---

### Post by fjgaude on 2008-01-26
Interesting, we learn new things day-by-day. Thanks for the heads up.

---

