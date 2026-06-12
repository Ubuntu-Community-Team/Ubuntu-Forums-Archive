---
title: "Is it possible to assoicate my box with a domain name if my ip address isn't static"
date: 2008-05-04
forum: General Help
---

### Post by voidstar on 2008-05-04
Hello everyone, I'm currently setting up ubuntu 8.04 on my new (refrub) box.  I plan on using it as a server for svn/trac and any web projects I'm messing around with.  I have a domain name already registered with dedicated hosting but they don't support running a svn or trac hosting.  And they don't have tomcat available.  So I'm just curious to see if it possible to somehow keep my changing ip address in sync with a dns server or if there are any workarounds possible.

Regards

Barry

---

### Post by fragos on 2008-05-04
The answer is DynamicDNS which is available as a free service on the web. Go to the link below and register -- free domains available. Then you add a bit of code to the boot process which will report your assigned IP to this company who will then update DNS for you. They have a number of free code snippets available.

[https://www.changeip.com/login.asp?](https://www.changeip.com/login.asp?)

---

### Post by voidstar on 2008-05-05
Thanks for the help, will try to set this up tonight

---

