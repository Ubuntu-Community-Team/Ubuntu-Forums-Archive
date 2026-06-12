---
title: "[SOLVED] dpkg Remove VYM deb Issue"
date: 2008-02-06
forum: General Help
---

### Post by galeg on 2008-02-06
Morning All
Downloaded vym-1.10.0-18.i586.rpm (applic View Your Mind rel 1.10.0) converted package to deb using Alien (result = vym_1.10.0-18_i386.deb), then ran -
$sudo dpkg -i vym_1.10.0-18_i386.deb
Unfortunately something screwed, and although I have a VYM ICON in the Open Office group, nothing actually happens when the ICON is selected. 
As a result I have decided to remove VYM and possibly try an earlier version 1.08.
My problem is, when I enter the command
$sudo dpkg -r vym_1.10.8-18_i386.deb I received the message back
"dpkg: you must specify packages by their own names, not by quoting the names of the files they come in¨
As the .deb file contained 2 x .gz files (and 1 x text file) are these the files the returned msg is referring too, as I was under the opinion the ¨dpkg"command looked at .deb files.
Any feedback would be appreciated.

---

### Post by Rocket2DMn on 2008-02-06
Try searching for it in Synaptic: System->Administration->Synaptic Package Manager.  You can remove it from there.  FYI, converting rpms to debs is not a perfect process, it does not work for everything.

---

### Post by galeg on 2008-02-06
Thanks
Removed with Synaptic Package Manager

---

