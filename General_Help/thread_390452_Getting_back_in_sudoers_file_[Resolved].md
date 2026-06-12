---
title: "Getting back in sudoers file [Resolved]"
date: 2007-03-22
forum: General Help
---

### Post by covetous_kid on 2007-03-22
Hi, 

I installed xbuntu dapper on my really old machine some time last summer but I haven't used it in about half a year.  Yesterday I decided to break it out so I could use it as a CVS server. But before I did that, I looked for a list of updates and installed something like 150 of them. I should have looked at the list of updates I installed because when I rebooted, I noticed that some of the settings have changed. Namely, I was no longer on the sudoers file. I figured this out when I tried to edit my boot options by writing to the menu.lst file, but it gave me "<my username> is not in the sudoers file. This incident will be reported." This is the only user on the machine. Is there a way I can get back in the sudoers file? 

Thanks in advance!

---

### Post by aysiu on 2007-03-22
Reboot into recovery mode, add your user to the *admin* group, then reboot to regular mode.

More details here:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by covetous_kid on 2007-03-22
Thanks! Worked like a charm :)

---

