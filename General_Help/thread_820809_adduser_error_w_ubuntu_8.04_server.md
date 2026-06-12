---
title: "adduser error w/ ubuntu 8.04 server"
date: 2008-06-06
forum: General Help
---

### Post by MystaMax on 2008-06-06
Hello, I'm trying to add some additional users to my ubuntu 8.04 server. The accounts are actually being added, but the `adduser` command doesn't ask for Full name, room number, work phone, and home phone like it is suppose to. I receive the following error after entering the new users' password:

Your account has expired; please contact your system administrator
chfn: PAM authentication failed
adduser: `/usr/bin/chfn $USERNAME' returned error code 1. Exiting.

I tried searching for the above error, and read over this thread ([http://ubuntuforums.org/showthread.php?t=296129](http://ubuntuforums.org/showthread.php?t=296129)), but it didn't provide me with an answer.

Any ideas?

---

### Post by zwilrich on 2008-09-09
I was having the same problem and this fixed it.

From [https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/238755](https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/238755)

This seems to be related to the use of "passwd -l root".
Until the Debian fix shows up in hardy, here is a workaround, thanks to Nicolas François:

 sudo passwd --unlock root
 sudo usermod --lock root

---

