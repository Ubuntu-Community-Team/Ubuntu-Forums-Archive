---
title: "Wget Mirroring Issue"
date: 2008-02-06
forum: General Help
---

### Post by davidwaizer on 2008-02-06
Hi,

Let me explain my situation; I need to download recursively the contents of a sub-directory on an ftp site, this sub-directory being called "Delivery":

[ftp://user:password@ftp.host.com/Delivery](ftp://user:password@ftp.host.com/Delivery)

So.. I'm using the following wget line to mirror that directory ( every day or so ) to my local drive:

wget -o logfile -N --server-response --no-remove-listing --mirror [ftp://user:password@ftp.host.com/Delivery](ftp://user:password@ftp.host.com/Delivery)

This seems to work fine, but looking at the logs I see that it spends an awful lot of time trying to get files that don't exist, here is an example:

--12:00:10--  [ftp://user:*password*@ftp.host.com/Delivery/subdir2/subdir3/Delivery](ftp://user:*password*@ftp.host.com/Delivery/subdir2/subdir3/Delivery)
           => `ftp.host.com/Delivery/subdir2/subdir3/Delivery'
==> CWD not required.
--> SIZE Delivery

550 Delivery: not a plain file.
--> PASV

227 Entering Passive Mode (1,1,1,1,1,0)
--> RETR Delivery

550 Delivery: No such file or directory.

No such file `Delivery'.

So, for some reason, it seems to be appending "Delivery" at the end of each URL that it finds to download and that obviously fails since the last subdirectory to download ( in this example ) is subdir3

Has anyone had this issue before? Do you have any suggestions that could help me?

Thanks!!!

Dave

---

