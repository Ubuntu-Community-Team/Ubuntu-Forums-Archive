---
title: "DPKG problems"
date: 2007-03-07
forum: General Help
---

### Post by chickensofdoom on 2007-03-07
The other day I attempted to install Beryl using the following tutorial:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

I got all the way to "Restart the X Server" without any problems. When I tried to do that, however, the system hung up, and I had to manually reboot and then manually do a fsck. I tried to do the next step (apt-get installing beryl), and found it gave me an error about a missing file: /var/lib/dpkg/available
There was a backed up version, available-old, which I tried copying and using, but that still gave me an error. I figured it was just a problem with the beryl install.

Then today I tried to do a system update, and it also gave me the error about the file missing.. apparently this is a rather essential file.  Any idea what I can do to set it right?

---

### Post by DagMan on 2007-03-07
Maybe one of these methods will get it back to normal.
[http://ubuntuforums.org/showthread.php?t=191323](http://ubuntuforums.org/showthread.php?t=191323)
[http://www.linuxquestions.org/questions/showthread.php?t=225508](http://www.linuxquestions.org/questions/showthread.php?t=225508)
I was just thinking that another thing to try would be to apt-get update with an empty sources.list file and then do it again with the normal one.

---

