---
title: "Clear space from terminal"
date: 2013-05-29
forum: General Help
---

### Post by mastertonone on 2013-05-29
I've been working on this for a few days and have Googled every possible resolution but I'm stuck. The original problem was Ubuntu 12.04 would load to the low graphics screen. I tried to run '[FONT=Ubuntu Mono]sudo apt-get install fglrx' but it says I have no space. So I run 'df' and it says /dev/sda1 has used 100%. I then use a number of 'du' commands to try and drill down to the file but I can't find anything in the /var or /tmp folders. If I check my home folder it says [/FONT]Total: 627459644 /home: 627459644. I sorted my files and deleted all the large files and it still says I have no space.  I'm at a complete loss of what is taking up all my space.

---

### Post by philinux on 2013-05-29
Have a look through here see if you missed something.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by mastertonone on 2013-05-29
Thanks. I was able to find the culprit... .xsession-errors. I'm working on clearing that now.

---

### Post by mastertonone on 2013-05-29
Ok I was able to get the .xsession-errors files clear away. After a restart it went straight into Ubuntu without the low graphics error.

---

