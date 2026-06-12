---
title: "pam nss and ldap servers"
date: 2008-05-20
forum: General Help
---

### Post by sangamc on 2008-05-20
I have successfully installed Fedora ds 1.0.4 on Ubuntu 8.04. I run into some issues when configuring Pam and Nss for the samba portion. On my first test server I was able to complete the setup without an y major problems. On all subsequent servers. I install FDS and successfully start the console and add one posix user.

I then begin installing Pam and Libnss by using the auth-client-config to automatically configure the files in /etc/pam.d/ as well as the nssswith.conf. after I do this, I can no longer log in to the console, and the error logs get filled with the following error.

[Mon May 19 00:43:26 2008] [notice] child pid 10675 exit signal Segmentation fault (11)

Can anyone point me in the right direction?

---

### Post by sangamc on 2008-06-04
bump!

anyone have any ideas that can help me solve this problem/ if more information is needed, someone let me know and ill post it

thanks

---

