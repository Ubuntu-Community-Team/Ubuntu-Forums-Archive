---
title: "Not upgrading a package"
date: 2007-10-22
forum: General Help
---

### Post by scottishnarn on 2007-10-22
I've recompiled celestia packages from source to get them to display some objects that don't work. However, apt-get and synaptic want to "upgrade" the version I've installed to the official one. It's exactly the same version, other than I've compiled it with an added compiler flag to get it work properly (following instructions on the Celestia forums). 

Is there any way to stop it being upgraded. Having searched the forums, I've already tried to lock the version in synaptic but this doesn't have any effect on the upgrade utility or apt-get. Another thread I looked at suggested that I set the version number artificially high. This sounds like a good idea but I have no idea how to do this. I just set a compiler flag and then did ```
dpkg-buildpackage -rfakeroot -uc -b
``` and installed the packages created, I don't know what files to alter to change the version number. 

Any help would be appreciated.
Thanks
David Petticrew

---

