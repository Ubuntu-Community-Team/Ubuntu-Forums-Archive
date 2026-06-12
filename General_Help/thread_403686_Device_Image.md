---
title: "Device Image"
date: 2007-04-07
forum: General Help
---

### Post by billdotson on 2007-04-07
I formatted my internal HDD, reinstalled Windows (nothing else i.e. programs, etc.) and then booted into Ubuntu (where I am now).

I want to use device image to backup my entire Windows partition which is /dev/sda1.
I ran the following command (in terminal):

```

zsplit -N WinXP_backup /dev/sda1

```

and I got this error message:

```

sgtmattbaker@sgtmattbaker:/$ zsplit -N WinXP_backup /dev/sda1
zsplit: version: 1.2.0
zsplit: start of operation
zsplit: read/write buffer size selected: 8 kibibyte (8192 bytes).
zsplit: compression level: 6.
zsplit: file/device-image cannot be splitted, size of chunk is unknown, one chunk image will be created
zsplit: cannot open file/device: /dev/sda1, in: treat_file()
zsplit: not succeeded..., error in operation!
zsplit: end of operation
sgtmattbaker@sgtmattbaker:/$ 

```

I have tried it doing 
```

zsplit -N WinXP_backup /dev/sda1

```
/dev/sda1 is NOT mounted when I tried this.

Then I tried the same command but w/ the drive being mounted..  same message

Then I tried the same command w/ the partition being mounted but I used it's mount point which is /media/Windows_ntfs.  Same error.  Also tried it w/ sda1 /dev/sda, and just sda.  Also tried it with my partitions on my external drive like /dev/sdb4 (unmounted and mounted)

Is there an easy fix to this?  I really would like to have my Windows install ghosted so that I don't have to worry about possible issues w/ the install.  

I have tried PartImage but I cannot trust it as the NTFS support is experimental.  I need a program that is a bit more reliable.

Thanks.

---

