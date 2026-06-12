---
title: "SSH from commandline with password"
date: 2007-04-10
forum: General Help
---

### Post by TheDigitalNinja on 2007-04-10
I need to find a way to specify both the user name AND password to use to connect to an ssh server. I know of the security issues but the user account has no privileges and all security is handled by software on the ssh server. In putty this can be done by "putty.exe 192.168.1.100 -p 22 -l user -pw password"

I need to have an icon on the desktop that the users can just double click and it will log into the ssh server where our custom software takes over and has them enter their credentials.

Should i use different ssh client on Linux? Is there a way im not aware of? Or should i just write an expect script?

---

### Post by stylishpants on 2007-04-10
You should set up passwordless logins.

[http://www.freebsdwiki.net/index.php/SSH:_Passwordless_authentication](http://www.freebsdwiki.net/index.php/SSH:_Passwordless_authentication)

---

