---
title: "fstab ruined in ecryptfs. Please help recovering"
date: 2015-01-12
forum: General Help
---

### Post by skamarla on 2015-01-12
Hello,

I was trying to setup a Samba share and I thought mountmanager would help. Boy, was I wrong. It didn't work (maybe because I didn't have cifs-utils installed, I don't know or care too much, I'm uninstalling it right away), and it overwrote my /etc/fstab.

I noticed on time, and tried to recover fstab by copying /proc/mounts back into /etc/fstab. But somehow, it didn't work out 100%, and the system doesn't start. What I'm doing right now is: I go into recovery mode, it prompts me for the ecryptfs options, it fails to mount my user's home filesystem on the first try, but it goes on. Then, I can logon normally, and my home partition is mounted; I can even access my files.

Can someone tell me what I should change in /etc/fstab for normal logon to take place? The relevant part of /etc/fstab is:

```
/dev/sda8 /home ext4 rw,relatime,user_xattr,acl,barrier=1,data=ordered 0 0
/home/joanc/.Private /home/joanc ecryptfs rw,relatime,ecryptfs_fnek_sig=96597ed
ffb6e7aa5,ecryptfs_sig=ff8ff46d973a16a8,ecryptfs_cipher=aes,ecryptfs_key_bytes=
16,ecryptfs_unlink_sigs 0 0
gvfs-fuse-daemon /home/joanc/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relati
me,user_id=1000,group_id=1000 0 0

```

Thanks in advance

---

### Post by skamarla on 2015-01-12
OK, fixed. Apparently, the encrypted devices in /proc/mounts don't get mounted from fstab. I commented out the two lines with my username (/home/joanc) and left just the /dev/sda8 for /home.

Now, it starts without any problems, and the ecryptfs gets mounted anyway.

I'll mark it as solved.

---

