---
title: "Show hidden files on Kubuntu"
date: 2007-07-10
forum: General Help
---

### Post by liberalist on 2007-07-10
Hi everyone,

How can I show hidden files on my Kubuntu 7.04 system? In KlamAV I namely see several folders of deleted programs with a dot (.) in front of their name. I wish to delete them. Furthermore, how can I hide hidden files again after deleting those files?

Thanks in advance.

---

### Post by rodo-&gt;dave on 2007-07-10
I don't have my ubuntu @work but I think there is an option on the "file manager" under preferences that will allow you to display 'hidden' files.

Also, at the cli you can type: ls -al 
to see all files...
but I don't know anything about clamav, so I am assuming you don't need something specific to that prog.
Later.

:)

---

### Post by kitterma on 2007-07-12
The files/folders with a leading dot are NOT deleleted.  They are system files that generally hold user configuration information.  Deleting them is not a good idea.

---

### Post by kuja on 2007-07-12
if you want config &c files to be removed when you remove it, you need to remove with the --purge option. (ie: dpkg --purge package or apt-get --purge remove package) Also, assuming you use Konqueror for file browsing, it's view -> show hidden files.

---

