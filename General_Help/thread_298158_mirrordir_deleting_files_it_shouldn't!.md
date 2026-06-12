---
title: "mirrordir deleting files it shouldn't!"
date: 2006-11-12
forum: General Help
---

### Post by abovett on 2006-11-12
I use mirrordir to sychronise important directories from my server (running SME Server) to my laptop. I've been doing it for years, but recently have noticed on my laptop (currently running Dapper) that some directories are getting deleted even though they exist on the source. What's more, they are files which have not been altered recently and have not changed since mirrordir was last run. It's unpredictable which files will get deleted and they normally get copied back on next time (but some other files may then get deleted).

I don't think this used to happen (though there might have been files I never looked at that got missed I suppose) but as it is mirrordir is useless to me as I can't trust it.

Anyone else seen this problem or have any idea why it should be happening? It's a bug somewhere of course but I'm not sure where.

To complicate things I am mirroring from a directory mounted using smbmount to a mounted FAT partition (because I sometimes have to access these files from Windows).

The mirrordir command I am using is:
```
mirrordir --no-chown --no-chmod --mtime-threshold 2 --case-insensitive -v /home/andrew/mnt/SOL/$share /mnt/win_e/$share
```
The FAT partition is mounted from fstab:
```
/dev/hda5       /mnt/win_e      vfat    auto,users,umask=0000,iocharset=iso8859-15,codepage=850,rw 0 0

```
The SMB share on the SME server is mounted using:
```
smbmount "$share" "$mountpoint" -o username=$username,workgroup=$workgroup,password=$password
```

Any suggestions greatly appreciated - I _really_ need to sort this.

Andy B

---

