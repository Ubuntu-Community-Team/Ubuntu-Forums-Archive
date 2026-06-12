---
title: "WPS Writer: permission denied to files on mounted device"
date: 2019-01-21
forum: General Help
---

### Post by marika.alicja on 2019-01-21
Hi,

I hope this is an acceptable place to post this question, did not find an adequate WPS forum for linux users.

WPS Writer has no access rights to my secondary HDD (mounted under /mnt), where I moved stuff after running out of space on my main drive: [https://www.dropbox.com/s/odqiw5tp8iiq09a/20190121071512.png](https://www.dropbox.com/s/odqiw5tp8iiq09a/20190121071512.png)
[IMG]https://www.dropbox.com/s/xdr9hr58lvv59v0/20190121072329.png[/IMG]


[LIST]
[*]Other files from said drive can be accessed with respective applications (WPS Spreadsheets, Notepadqq, Nautilus file manager..)
[*].docx files from said drive can be accessed with LibreOffice Writer (snap)
[*]I am the owner:
[/LIST]
```
[INDENT]marika:/mnt/1TB $ ls -l[/INDENT]
[INDENT]-rw-r--r--  1 marika marika 386617 lis 29 10:14 notes.docx[/INDENT]

```
[LIST]
[*]WPS Office has been given permissions in Ubuntu Software: [https://www.dropbox.com/s/xdr9hr58lvv59v0/20190121072329.png]("https://www.dropbox.com/s/xdr9hr58lvv59v0/20190121072329.png?dl=0")[IMG]https://www.dropbox.com/s/xdr9hr58lvv59v0/20190121072329.png[/IMG]
[*]Same .docx files can be accessed when copied back to /home
[/LIST]


Any ideas?


Thx,
Marika

---

### Post by anonymbruker on 2019-01-31
I have a similar issue.
I have mounted a OneDrive with rclone, but is not able to access it.
I get a "Permission denied".
The permissions and attributes are just the same as for other files, and I can access the files with other applications, like the built-in Text Editor.

---

### Post by tamkaho on 2019-09-29
Have you managed to solve this?

---

### Post by TheFu on 2019-09-29
It is the permissions on the snap package, nothing wrong with your file permissions.
Snaps run in a protected space and some of the access rights provided by default are much to limiting.  Open a bug in Launchpad to complain or this will never be fixed.   Heard that 19.10 will have as many packages installed as snaps as possible. This isn't going to get better.

IMHO.

There are many overly restrictive settings in current snaps that need to be handled.

Or you might be able to remove the snap package and install the normal package. Just don't use software center to do the install, use APT.

[https://snapcraft.io/blog/demystifying-snap-confinement](https://snapcraft.io/blog/demystifying-snap-confinement) explains the confinement.
[https://tutorials.ubuntu.com/tutorial/basic-snap-usage#0](https://tutorials.ubuntu.com/tutorial/basic-snap-usage#0) is the basic snap tutorial. Modifying confinement is in the advanced tutorial, which is linked at the end of the basic tutor.

---

