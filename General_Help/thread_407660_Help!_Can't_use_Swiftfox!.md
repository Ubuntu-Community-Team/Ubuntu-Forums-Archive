---
title: "Help! Can't use Swiftfox!"
date: 2007-04-12
forum: General Help
---

### Post by RJARRRPCGP on 2007-04-12
Here's the output: Here's the errors I'm getting:
Installing Swiftfox...
mv: cannot stat `swiftfox': No such file or directory

bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error exit delayed from previous errors
 
Searching for existing plugins, errors can be safely ignored...
cp: cannot stat `swiftfox.old/plugins/*': No such file or directory
cp: target `swiftfox/plugins' is not a directory
cp: target `swiftfox/plugins' is not a directory
cp: target `swiftfox/plugins' is not a directory
cp: cannot stat `/usr/lib/browser-plugins/*': No such file or directory
chown: cannot access `swiftfox': No such file or directory
--12:04:37--  [http://getswiftfox.com/builds/installer/Swiftfox.desktop](http://getswiftfox.com/builds/installer/Swiftfox.desktop)
           => `Swiftfox.desktop'
Resolving getswiftfox.com... 208.113.142.250
Connecting to getswiftfox.com|208.113.142.250|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 412 [text/plain]

100%[====================================>] 412           --.--K/s             

12:04:39 (21.83 MB/s) - `Swiftfox.desktop' saved [412/412]

 
Swiftfox 2.0.0.3 has been installed. Happy Surfing!
 
rjarrrpcgp@RJARRRPCGP-PP:~/Desktop$

The above error messages are despite I let the download finish! Downloaded 8 MB or around 8 MB just to get those errors! :evil:

---

### Post by dbbolton on 2007-04-12
are you running the installer as root ?

---

### Post by RJARRRPCGP on 2007-04-12
> **dbbolton said:**
> are you running the installer as root ?

Yep, I was running as root. I used```
sudo sh install-swiftfox.sh
```

How can delete those files? I can't find them! I want to delete them so I can redownload it!

---

### Post by dbbolton on 2007-04-12
they should be in your home folder...

---

### Post by RJARRRPCGP on 2007-04-12
I'm talking about the archive files that the installer downloads. I'm I gonna be required to reformat and reinstall?

---

### Post by Stirling on 2007-04-12
The installer removes the tarball when it's done.  Sounds like you got a corrupted tarball, I would try running the installer script again.

---

### Post by shirilover on 2007-04-12
The easiest way to install swiftfox is to either use the swiftfox repository or the deb files available here -> [http://www.getswiftfox.com/debian.htm](http://www.getswiftfox.com/debian.htm)

---

### Post by RJARRRPCGP on 2007-04-12
> **Stirling said:**
> The installer removes the tarball when it's done.  Sounds like you got a corrupted tarball, I would try running the installer script again.



That occurred, because I stopped the download, but I let it finish later. It won't delete the cut off tarball files in the /opt directory when I use ctrl+c. 

But the Swiftfox installation was successful with Automatix. Even when I didn't delete the extraneous tarball files in the /opt directory.

---

