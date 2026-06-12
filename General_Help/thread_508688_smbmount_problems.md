---
title: "smbmount problems"
date: 2007-07-24
forum: General Help
---

### Post by hatzilim on 2007-07-24
Hi all,

I am having trouble with smbmount.

I am able to access a directory using smbclient. The root directory of the share I am connecting to does not allow its directory to be listed. The directory that I want is a sub-sub directory.

so I do something like this:

smbclient //servername/share -U username

and then cd /some/deep/directory

and I can see my files.

I want to replicate this with smbmount:

smbmount //servername/share /mnt/mountpoint -o username=username

It does connect, but I cannot list the directory, nor change to my directory.

any ideas?

Thanks,

Jason

---

