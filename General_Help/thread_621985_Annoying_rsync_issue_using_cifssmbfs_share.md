---
title: "Annoying rsync issue using cifs/smbfs share"
date: 2007-11-24
forum: General Help
---

### Post by bleearg on 2007-11-24
Hi all,
I'm having a very annoying problem that's started occurring since my upgrade to Gutsy from Edgy.  I have two copies of my music share - one on my local drive and one on a Linkstation NAS.  I am currently mounting the network drive through fstab as such:

```
//172.16.28.8/music /home/myname/music  cifs     credentials=/root/.smbcredentials,uid=myname,gid=myname,file_mode=0777,dir_mode=0777,iocharset=utf8   0       0
```

Mounting works fine, as do the permissions - no problems there. I often put files into the local directory (/backup/music_local) where I can modify them to my liking, then rsync them over to the remote directory:

```
rsync -avu /backup/music_local/ /home/myname/music/
```

Ever since my upgrade to Gutsy, the rsync keeps attempting to copy the same files over, as though they are either missing, not updated, or different than the file that's on my local machine.  I've gone so far as to remove the files locally, copy them *from* the share to my local machine, then perform an rsync from the local machine to the share, and the same thing happens; the exact same files attempt to get copied.

Anything I'm missing here?

---

### Post by gmaniac on 2007-11-24
I don't know but could it be caused by a time difference between nas and your computer?

---

### Post by vanadium on 2007-11-24
Indeed, try the --modify-window=1 option (see man rsync for detail)

---

### Post by bleearg on 2007-11-25
Interesting.  I used the '--modify-window=1' and no files showed up as needing to be copied.  I had assumed that the NAS was set to the same time as my machine, as they're both synced up using NTP, plus the file mod dates both show the same times.  However, when I logged onto my NAS, it was a week behind :confused:.  However, problem still happens, but not if I use the above option.

Searching around, I see that this is a common problem when syncing to SAMBA shares, but it seems  that it's usually attributed to Windows shares and my NAS is XFS, I believe.  Anyway, I'm not concerned about that.  What's strange is that it just started happening with my upgrade to Gutsy.  Again: :confused:

Thanks for the tip!

---

