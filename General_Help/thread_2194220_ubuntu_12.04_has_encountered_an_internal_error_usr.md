---
title: "ubuntu 12.04 has encountered an internal error /usr/bin/sshd"
date: 2013-12-17
forum: General Help
---

### Post by morphyrichards1 on 2013-12-17
I have an AMD 64 based installation of Edubuntu 12.04 in my classroom. There is also Zentyal file/authentication server on the network.
It is acting as a server / router to 30 raspberry pi computers (15 per subnet on two seperate NICs)

It is also an LTSP server, but usual use is for students to log in to a raspberry pi normally with logins using LDAP.

I've configured the edubuntu server as suggested here: [https://help.ubuntu.com/community/UbuntuLTSP/ThinClientHowtoNAT/](https://help.ubuntu.com/community/UbuntuLTSP/ThinClientHowtoNAT/)

The raspberry pi computers have LDAP configured as suggested here: [http://forum.zentyal.org/index.php/topic,12925.msg66997.html#msg66997](http://forum.zentyal.org/index.php/topic,12925.msg66997.html#msg66997)

When logged into a raspberry pi, if I then ssh into my server, say I do this:

ssh -X testuser@ubuntuserver
and do some stuff, say use libreoffice.
When I come out again there is an internal error on the edubuntu server: "ubuntu 12.04 has encountered an internal error" /usr/bin/sshd 
It seems sshd is causing a crash.

Additionally, a number of users using LTSP can cause the whole server to suddenly reset. I wonder if this is related?

Any ideas what could be causing this to happen?

Thanks in advance.

---

### Post by morphyrichards1 on 2013-12-17
additonal: the error report states sshd crashed with SIGSEGV in vfprintf()

---

