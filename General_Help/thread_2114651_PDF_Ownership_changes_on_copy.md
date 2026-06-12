---
title: "PDF Ownership changes on copy"
date: 2013-02-10
forum: General Help
---

### Post by foberle on 2013-02-10
I have several ntfs partitions shared between Windows and Ubuntu (12.04.1), and so far that hasn't proved to work in any way I wasn't expecting. But it's tax time here in the U.S., so I downloaded the forms I need as pdf files that can be filled in.
Naturally they download to the normal Ubuntu Downloads folder.
When I copied them to the shared folder where I keep such things, I found that I was unable to save them - Ubuntu telling me that I was not the owner. And indeed, they show up as root for both group and owner.
However, when I went back to the originals in the Downloads folder and copied them to Ubuntu's own Documents folder, they show up with me as the owner, and I am able to edit and save them successfully. My conclusion is that there's nothing amiss with the pdf files themselves, and nothing amiss with the copy function, but that the issue is with the fact that I'm using a mounted ntfs partition.
I attempted to "sudo chown" the files on the ntfs drive, which doesn't return any error at the command line, but doesn't seem to do anything.
What gives? How do I correct this? Of course I'm not that eager to pay my taxes, but I don't think the IRS will accept "I use Ubuntu" as a way to dodge them. Any help would therefore be appreciated.

---

### Post by schragge on 2013-02-10
You can set uid and gid options when mounting an NTFS volume, e.g in /etc/fstab
```

UUID=B6F8D315F8D2D2AB  /mnt/winxp ntfs  fmask=111,uid=1000,gid=1000     0 0

``` Obviously, values for UUID, mountpoint, UID and GID must be yours

---

### Post by foberle on 2013-02-11
Thanks much - adding the uid=1000 and gid=1000 entries seemed to do the trick.
For others reading this, the id 1000 is assigned to the user who initially did the installation and, for those of us who are the sole users of the machine, this will work.

---

