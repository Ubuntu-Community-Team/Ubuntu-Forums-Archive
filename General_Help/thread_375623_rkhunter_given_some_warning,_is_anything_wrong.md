---
title: "rkhunter given some warning, is anything wrong?"
date: 2007-03-04
forum: General Help
---

### Post by say2sky on 2007-03-04
I gotten is info about hidden directory on the dapper machine.  do I need to delete these hidden directory or just keep them.

[12:54:41] WARNING, found:  /etc/.java (directory)  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)

---

### Post by smdeep on 2007-03-22
Hi
I get the same warning on two servers, could someone help please?

thanks in advance

---

### Post by floke on 2007-03-22
99% certain its fine - the check picks up on empty directories and a few other oddities, so unless you fine-tune the check it chucks out a number of false positives.

---

### Post by smdeep on 2007-03-22
Thanks
Found another thread which suggests using [http://www.ossec.net/](http://www.ossec.net/)

---

