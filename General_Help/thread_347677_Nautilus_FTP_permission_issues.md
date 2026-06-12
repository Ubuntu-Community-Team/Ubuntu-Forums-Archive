---
title: "Nautilus FTP permission issues"
date: 2007-01-27
forum: General Help
---

### Post by yigal.weinstein on 2007-01-27
In a terminal ftp is a cake walk: 
```
$ftp
```
enter username
```
$username
```
password
```
$password
```
I am sitting pretty using command like put and get to my harts content.

Nautilus is a whole other story:
File ---> Connect to Server:
FTP (With Login)
then I fill out my info.  I get into my "home" folder.  There are 2 folders and an html file. 

1.  I open the file with gvim with a right click of my mouse.  Gvim requires that I issue my password again.
2. I try and delete the html file by dragging it to the trash can. Access Denied.
3. Cannot move into either of the 2 folders in my home directory.

What is up with the permissions in Nautilus with FTP?  :confused: :mad: 
This has been an ongoing problem from a nieve google search since at least Gnome 2.11 and I am pretty sure it has something to do with libgnome2-vfs and virtually nothing to do with Ubuntu.   

For instance I see this in Hoary:
[https://launchpad.net/ubuntu/+source/nautilus/+bug/19248](https://launchpad.net/ubuntu/+source/nautilus/+bug/19248)

Can someone help me to make Nautilus usable as a ftp client.  Thanks best.

---

### Post by yigal.weinstein on 2007-01-27
I have resolved some issues by myself.  I used gftp to visit my ftp home and it told me that my home, i.e. <ftp.server.com>/home was in fact a link of sorts to another location.  I have now successfully connected with Nautilus to this new location and can now at least copy files between computers with Nautilus via ftp.

So my problem is 2 fold now:

1. Nautilus seems not to know how to use an ftp link - I don't know whether this is a hard or symbolic link or exactly but it is a link.
This may be related to the bugzilla report: [http://bugzilla.gnome.org/show_bug.cgi?id=331684](http://bugzilla.gnome.org/show_bug.cgi?id=331684)

2. permissions of files are not displayed and certainly not alterable via Nautilus.

---

