---
title: "Snap package telegram no longer works"
date: 2016-06-23
forum: General Help
---

### Post by dom134 on 2016-06-23
I installed the telegram snap a few weeks ago, but at some stage it stopped working.  I tried to remove it, but got the following responses
> dom134@ubuntu:~$ snap list
error: cannot list snaps: cannot list local snaps! cannot find mounted snap "telegram-sergiusens" at revision 3

dom134@ubuntu:~$ sudo snap refresh
error: cannot list updates: cannot list snaps: cannot list local snaps: cannot find mounted snap "ubuntu-core" at revision 109

I am on 16.04 Unity

And just for completeness:
> dom134@ubuntu:~$ sudo snap remove telegram-sergiusens
error: cannot remove "telegram-sergiusens": cannot find mounted snap "telegram-sergiusens" at revision 3

dom134@ubuntu:~$ sudo snap install telegram-sergiusens
error: cannot install "telegram-sergiusens": snap "telegram-sergiusens" already installed

Any help greatly appreciated

---

### Post by QDR06VV9 on 2016-06-23
This is a bug:[https://bugs.launchpad.net/snappy/+bug/1571721](https://bugs.launchpad.net/snappy/+bug/1571721)

---

### Post by dom134 on 2016-06-23
Superb, thank you!

I ran the script at [https://github.com/zyga/devtools/blob/master/reset-state](https://github.com/zyga/devtools/blob/master/reset-state) to reset my snaps and it is working now.

Thanks

---

### Post by QDR06VV9 on 2016-06-23
Nice Work! Glad it worked out for you.:D
Kind Regards

---

