---
title: "Sudo command gives no response [Resolved]"
date: 2007-03-10
forum: General Help
---

### Post by ssjoholm on 2007-03-10
Hi,

I have a fresh install of Ubuntu 6.06 LTS, and got problems with sudo, after the installation sudo worked fine as it should. But after while I stopped to get any response from it (look example below). I have searched for answers, but been unable to find any, as so many posts include the sudo word so the hits are quite many.

example;

admin@ubuntu:/$ sudo cat /etc/sudoers
admin@ubuntu:/$ sudo shutdown -r now
admin@ubuntu:/$ sudo shutdown -r now
admin@ubuntu:/$ sudo shutdown -r now
admin@ubuntu:/$ sudo shutdown -r now
admin@ubuntu:/$ sudo shutdown -r now
admin@ubuntu:/$ sudo reboot
admin@ubuntu:/$ sudo reboot
admin@ubuntu:/$ sudo reboot
admin@ubuntu:/$ sudo pico /etc/sudoers
admin@ubuntu:/$ sudo pico /etc/sudoers
admin@ubuntu:/$ sudo pico /etc/sudoers
admin@ubuntu:/$

No known changes regarding sudo has been done, it just stopped giving output. It seems like it was hanging the whole function.

root account is not activated.

Best regards,
Sebastian

---

### Post by ssjoholm on 2007-03-10
Found more information in following post:

[http://ubuntuforums.org/showthread.php?t=379677]("http://ubuntuforums.org/showthread.php?t=379677")

The link above gives more information about the problem.

I was able to solve it by booting the system with the UBUNTU CD, and choose rescue mode. Started shell on the original harddisk and was able to give root user password (passwd root) and add myself to the admin group. After the reboot sudo worked as it should again.

Regards,
Sebastian

---

