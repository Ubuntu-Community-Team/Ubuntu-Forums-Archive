---
title: "chmod behavior changed??"
date: 2014-05-21
forum: General Help
---

### Post by jdmccue927 on 2014-05-21
I need access to a drive. I had access in 13.10 but cannot get it back in 14.04. I keep getting "You do not have the permissions necessary to view the contents of “TDrive”"  It is an mtfs drive that I share with some Windows boxes and also have nfs set up for it. EVERYTHING is denied. 
fstab:
```
UUID=****6D7  /TDrive  ntfs-3g defaults,user,uid=1000,gid=1000,umask=777,dmask=777,fmask=777,utf8  0
```

exports:
```
/TDrive       *.*.*.0/255.255.255.0(rw,nohide,insecure,no_subtree_check)
```


finally trying to change permissions from treminal i.ie

```
>sudo chmod 777 TDrive
```

results in:
```
d---------   1 * *  8192 Mar 14 14:56 TDrive
```

What the... is going on???

Can anyone help with this? ANY suggestion useful. Thanks in advance.

---

### Post by coldcritter64 on 2014-05-21
umask of 777 = permissions of 000, that is NO-ONE will access that volume until changed. If you want 644 permissions umask settings would need to be 233. You subtract the umask setting from 777 to get the final permissions settings. Same for dmask (d for directories) and fmask (f for files), 777 is effectively killing off your permission to access for anyone to either directories or files. If you use dmask and fmask you really don't need a umask setting, using dmask and fmask should give you finer control over the permissions.

Remember chmod sets whatever you input for the permissions directly, masking subtracts the "u","d" or "f" mask value from fully open permissions of "777".

Edit: I should also note using chmod only sets the permissions for the mountpoint in Ubuntu, when the mount options take over for the ntfs volume mounting that chmod setting gets overridden.

---

### Post by HiImTye on 2014-05-22
chmod won't work for non-Linux filesystems since they handle permissions differently. you need to set your permissions at mount time, and remember that masks are backwards

---

### Post by jdmccue927 on 2014-05-23
Thank you to both coldcritter64 and HimTye! I think getting reversed on the masks was the major issue. Its so great to have a second (thousand) pair of eyes. Now I can stop banging my head.

---

### Post by coldcritter64 on 2014-05-23
If it works ok, please remember to mark as solved, thanks. There's a link in my sig line if needed. Cheers.

---

