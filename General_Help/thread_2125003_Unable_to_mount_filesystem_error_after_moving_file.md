---
title: "Unable to mount filesystem error after moving files?"
date: 2013-03-12
forum: General Help
---

### Post by AkaCrabby on 2013-03-12
I'm still new to Linux in general and am really not sure what to do from this point. I was moving a ~600mb TV show to my media drive and as soon as it finished it gave this error:
```

Unable to mount Media


Error mounting /dev/sdb1 at /media/evan/Media: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/evan/Media"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
The drive still comes up in gnome-disks and it doesn't say anything's wrong with it but when I mount it it continues to give that error. If I could fix this that'd be great, but if I could just pull the files off and put them on another drive that'd be just as fine; I guess now's a great time to get that 1TB drive I've been eyeballing. I ran df -h earlier today and it was 76% full with ~68GB free. I've also provided screenshots of both the error and gnome-disks. Thanks in advance to any form of help!

---

