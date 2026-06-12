---
title: "Ubuntu 7.04 Remote desktop connection with sessions. How?"
date: 2007-08-25
forum: General Help
---

### Post by Akula on 2007-08-25
Hello everyone!

I need to open remote desktop connection (with sessions so that account name and password are asked on beginning of each remote session) from my windows XP desktop to Ubuntu 7.04 server with ubuntu desktop installed on it.

I have tried System -> Administration -> Login Window and enabling Remote. With this configured I can connect to my server using vncviewer, but with no sessions. I have also looked for answer from this forum but none of them have worked out.

For example this thread seemed to work for many but not for me. I think it was mentioned that 7.04 has bug on it so I only get EndOfStream errors after login:
[http://ubuntuforums.org/showthread.php?t=42941&highlight=desktop+remote+gdm](http://ubuntuforums.org/showthread.php?t=42941&highlight=desktop+remote+gdm)

Anyone could help me?
Thanks in advance!

---

### Post by Akula on 2007-09-07
Anyone?

---

### Post by bmorency on 2007-09-07
I think what you are looking for is NX. you can get it from nomachine.com [here.]("http://www.nomachine.com/download-package.php?Prod_Id=1") I am using it on my system right now. it works great. it is a lot faster than vnc.  when you connect it will ask you for your username and password and start a new session.

it's been a while since i have installed but I think you have to install the linux client first then the node than the server so all the the files are there before the server is started.

---

### Post by Akula on 2007-09-09
Thanks. This seems to work nicely =)

---

