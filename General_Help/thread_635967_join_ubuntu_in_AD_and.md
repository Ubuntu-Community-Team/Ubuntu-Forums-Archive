---
title: "join ubuntu in AD and"
date: 2007-12-09
forum: General Help
---

### Post by tanveer on 2007-12-09
Hi all,
I have joined ubuntu with windows server 2003. Thanks to the author of this tutorial. I followed this link for doing this: [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

Now the problem is whenever I try to access anything it keeps asking me for password like to mount the users home folder from windows domain, file server, integrate with exchange with evolution it keeps asking for password on and on. How to stop that?

How to make samba service start before winbind as both of them set to S20samba && S20winbind.

Please let me know anything that can help.

waiting for your kind response.

---

### Post by monktbd on 2007-12-09
just give the service you want to start earlier a lower number, e.g. S19samba or the one youp want to start later a higher number like S21winbind.

the only problems that i can think of that might occur is that you might also need to adapt the shutdown number (stop the later started one before the earlier started one with the respective k##smaba command) and that when uninstalling the service it might not find the changed S##samba script for removing.

---

### Post by tanveer on 2007-12-09
Thanks a lot.I will give that a try.
What about the password prompting issue regarding joining to AD? Any idea/suggesstion on that to overcome?

thanks.

---

### Post by tanveer on 2007-12-10
Say After joining in AD, I configured evolution to get mails from exchange server. At the first time it asks for password, which seems ok. But, if I close the evolution and open again it again asks for password. Even After PC reboot when I again open evolution it asks for password again. Interesting thing is even to compose/reply you have to give your password.

Also. If I want to enter in file server of windows 2003 it also asks for password everytime.

Any idea how to overcome this??? Is LDAP required to overcome this?

thanks for your valuable time.

---

### Post by tanveer on 2007-12-10
Say After joining in AD, I configured evolution to get mails from exchange server. At the first time it asks for password, which seems ok. But, if I close the evolution and open again it again asks for password. Even After PC reboot when I again open evolution it asks for password again. Interesting thing is even to compose/reply you have to give your password.

Also. If I want to enter in file server of windows 2003 it also asks for password everytime.

Any idea how to overcome this??? Is LDAP required to overcome this?

thanks for your valuable time.

---

### Post by tanveer on 2007-12-12
Hi,
Attached the screenshot I used to get everytime I try to connect to file server mount points, evolution..etc.

---

### Post by tanveer on 2008-01-06
Problem solved for file shares but persists on password prompting for Evolution on each startup of evolution.

---

