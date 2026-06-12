---
title: "&quot;Logout (End Session)&quot; doesn't work as expected after upgrade to 18.04."
date: 2018-08-24
forum: General Help
---

### Post by sowani on 2018-08-24
Hi,

After upgrading from 16.04 to 18.04, Leave >> "Logout (End Session)" doesn't work as earlier. In 16.04, it used to show login screen again. After upgrade to 18.04, it re-logs in automatically. How to fix this issue? Please help.

Thanks,
Atul.

---

### Post by sowani on 2018-08-25
The cause was insertion of following lines to /etc/pam.d/lightdm after upgrading 16.04 to 18.04:

session optional        pam_kwallet.so auto_start
session optional        pam_kwallet5.so auto_start

I commented out these two lines as follows:

#session optional        pam_kwallet.so auto_start
#session optional        pam_kwallet5.so auto_start

Now the logout behaviour seems to be correct.

Following link helped in resolving this issues:
[https://askubuntu.com/questions/1062099/kubuntu-16-updates-forces-login-immediately-after-logout](https://askubuntu.com/questions/1062099/kubuntu-16-updates-forces-login-immediately-after-logout)

---

