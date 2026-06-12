---
title: "Apt offline help"
date: 2005-09-30
forum: General Help
---

### Post by ArthurHeng on 2005-09-30
[http://www.batmat.net/apt-offline/ch2.html#s2.2](http://www.batmat.net/apt-offline/ch2.html#s2.2)

Now Im following this guide to make apt retrieve deb packages locally, I retrieved all those necessary .deb files using wget, stored it in a folder. I configured the apt.conf, typed in the commands, but it still wont work. The error message is : 
(using xpdf as an example, I have the necessary deb files for xpdf)
"Reading package lists... Done
Building dependency tree... Done
Package xpdf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list file: hoary/main Packages (/mnt/xxx/lists/_mnt_xxx_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list file: hoary/restricted Packages (/mnt/xxx/lists/_mnt_xxx_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package xpdf has no installation candidate
"

can someone tell me how to properly configure my sources.list? Currently I commented all links to prevent apt-get from getting files from the net. the only uncommented line is this "deb file:/mnt/xxx hoary main restricted", there must be something wrong with this line.

Also, It told me to "copy /var/lib/dpkg/status to it", but my status file does not match with the deb files in my disk, what should i do so that descriptions in status file matches deb files stored locally?

---

### Post by ArthurHeng on 2005-09-30
Oh, and this is the error message when I typed in "apt-get update"

"
Ign file: hoary Release.gpg
Ign file: hoary Release
Ign file: hoary/main Packages
Ign file: hoary/restricted Packages
Err file: hoary/main Packages
  File not found
Err file: hoary/restricted Packages
  File not found
Failed to fetch file:/mnt/xxx/dists/hoary/main/binary-i386/Packages.gz  File not found
Failed to fetch file:/mnt/xxx/dists/hoary/restricted/binary-i386/Packages.gz  File not found
Reading package lists... Done
W: Couldn't stat source package list file: hoary/main Packages (/mnt/xxx/lists/_mnt_xxx_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list file: hoary/restricted Packages (/mnt/xxx/lists/_mnt_xxx_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
"

---

### Post by heimo on 2005-09-30
Maybe this thread can help you:
[http://www.ubuntuforums.org/showthread.php?t=42862](http://www.ubuntuforums.org/showthread.php?t=42862)

---

### Post by ArthurHeng on 2005-09-30
Thanks a bunch man!

---

