---
title: "Is it possible to permit users to add files but not overwrite/delete/rename?"
date: 2008-05-13
forum: General Help
---

### Post by ruipedroca on 2008-05-13
Hi,

Is is possible to permit users to add files to a directory, but not overwrite/delete/rename the files already existing (in a samba or vsftp server)?

Thanks,

---

### Post by bodhi.zazen on 2008-05-13
Yes, with a "sticky bit"

[http://www.linuxdevcenter.com/pub/a/linux/lpt/22_06.html](http://www.linuxdevcenter.com/pub/a/linux/lpt/22_06.html)

[http://www.zzee.com/solutions/linux-permissions.shtml#setuid](http://www.zzee.com/solutions/linux-permissions.shtml#setuid)

---

### Post by ruipedroca on 2008-05-13
Hi, bodhi.zazen

Thanks for your reply!

But how can i prevent the same user that created the files to rename/delete them? Can this be accomplished?

Regards,

---

### Post by bodhi.zazen on 2008-05-13
You would have to change the ownership of the file. You could do it easiest with a cron job ...

Alternate would be to change the umask value of the user in .bashrc, but that would be a pain and if you did not change ownership users could change permissions of the file back to rw ...

---

### Post by ruipedroca on 2008-05-13
Hi, bodhi.zazen

The cron job is a very good idea! :KS
I don't mind if users make changes within the same day, in fact, it comes handy! The next day it mustn't be allowed!
So, a cron job running during the night is a very good solution (a command changing the files owner).

Thanks one more time! :guitar:
Regards!

---

