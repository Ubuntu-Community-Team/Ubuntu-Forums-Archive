---
title: "ls: Cannot open directory &quot;budget&quot;: Permission denied"
date: 2019-07-24
forum: General Help
---

### Post by mel-blanc on 2019-07-24
Ubuntu 19.04 desktop

I have a directory:                  /image/budget

Running 'ls' command returns the message that "ls: cannot open directory 'budget': Permission denied"

Other directories can be listed normally with the typical 'ls -al' command.

Checked permissions and found 0775. Decided to live dangerously and changed to 0777. Still no joy.

Checked to be sure that selinux was disabled. Ran 'sestatus' and 'Disabled' was returned. Then ran
ls -alZ to see if any contexts were associated with the directory but only a '?' appeared in the 
column for context information.

As a trial I changed 'setuid' and 'setgid' to 1 so that I had either 1777, 4777 or 7777 for permissions
but still no joy. Returned permissions to 0777.

I have tried this as the user, sudo and root. 

Are there any other directory or file settings to check which will block listing a directory?

Thanks

Mel

---

### Post by TheFu on 2019-07-24
A failing disk.
ACLs.

But it sounds more like corruption.  I'd run fsck.

Which file system does it have?

---

### Post by mel-blanc on 2019-07-24
> **TheFu said:**
> A failing disk.
ACLs.

But it sounds more like corruption.  I'd run fsck.

Which file system does it have?

The filesystems is ext4. I will give e2fsck a run again.
Thanks

---

### Post by TheFu on 2019-07-24
Have you checked the SMART data for the disk?  That could point to a reason for corruption. It could just be a bad cable, for example. The SMART data shows that differently from bad disk sectors.

Ubuntu doesn't have SELinux.  I suppose it is possible to install SELinux on Ubuntu, but it wouldn't be by accident and I doubt it would be trivial.  I've never seen apparmor cause any issues.

---

### Post by mel-blanc on 2019-07-25
Morning Fu

Thanks for the feedback. I will give it a try.

Regards

Mel

---

