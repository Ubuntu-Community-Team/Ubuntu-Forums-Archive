---
title: "Truecrypt mounting in 7.04"
date: 2007-08-04
forum: General Help
---

### Post by Michaelg14 on 2007-08-04
Sorry about the double post

I use 7.04 and Truecrypt for that and windows.  I have a volume created under windows that uses a keyfile.  Whenever I try to open the volume I get an error that says something like unexpected error code.

How do I mount this volume?

Thanks

---

### Post by Trevster on 2007-08-05
Check out this link. [http://www.truecrypt.org/docs/](http://www.truecrypt.org/docs/) on the left there is a link for linux documentation.

You need to specify the file to mount, any options like ntfs support and where to mount it. Something like this:

truecrypt --mount --filesystem ntfs-3g /media/files/"thetruecryptfilename"  /mnt/tc/ #the mount point.

If it's an encrypted partition or device then specify it's location like /dev/sda6 for example.

I don't use a keyfile but the option is -k
-k, --keyfile FILE | DIRECTORY

---

