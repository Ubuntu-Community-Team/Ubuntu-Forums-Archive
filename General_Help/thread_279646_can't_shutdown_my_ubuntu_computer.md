---
title: "can't shutdown my ubuntu computer"
date: 2006-10-18
forum: General Help
---

### Post by frank05 on 2006-10-18
I type sudo shutdown -r now at the command prompt and the shutdown program just hangs. It is listed in the process table as sleeping.

Any ideas where to start on finding the cause of this? I've tried looking in various system log files but couldn't find anything.

Thanks

---

### Post by anaconda on 2006-10-18
Does 
sudo reboot
work?

---

### Post by hillbilly on 2006-10-18
hmm...try 
> sudo shutdown -r -t 0 now

And i thnk shutdown -r is a reboot command :?!! This is what i usually use to shutdown my ubuntu system
> sudo shutdown -h -t 0 now

---

### Post by frank05 on 2006-10-24
@anaconda and hillbilly

both those commands you list do not work, although they should normally (they hang just like i described above). Curiously, entering init 0 and init 6 shutsdown and reboots the system respectively. If anyone has any idea what could have happened to my system I'd like to know! :)

Thanks,

---

### Post by az on 2006-10-24
Sounds like a bug.

---

