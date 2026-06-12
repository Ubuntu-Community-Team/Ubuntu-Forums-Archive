---
title: "errore: login incorrect"
date: 2013-11-19
forum: General Help
---

### Post by pinolo on 2013-11-19
in a machine on a local network is now impossible login with any user of the network. (I think it happened after I removed the root user).
Anytime a user tries to login, the result is: "Login incorrect". Of course it's impossible to connect also via ssh, and the error in this case is [COLOR=#101010][FONT=Ubuntu]"Permission denied, please try again."[/FONT][/COLOR]
It's a machine with ubuntu 12.04 (upgraded from 10.04).
I tried with the guides i found on google, but with no result...
How can I solve that?
thank you!

---

### Post by steeldriver on 2013-11-19
How exactly did you "remove the root user"?

---

### Post by pinolo on 2013-11-20
ok, it was a normal user with sudo/admin privileges, and it was a local machine user, not a network user.
it's been removed with the command "userdel root_username".
the network users use NIS service to login, and in that machine I see that some files, like nis file in /etc/default have disappeared. it's very difficult fix things since I cannot login with any user on that machine. but, of course, i can use a live CD for modifying files. I tried to substitute securetty, shadow, shells, passwd files with the respective ones taken from a working machine of the same network, but it was unsuccesful.

---

