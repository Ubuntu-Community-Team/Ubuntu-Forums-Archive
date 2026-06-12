---
title: "how to give permission a file to execute"
date: 2008-01-16
forum: General Help
---

### Post by taimur on 2008-01-16
hi i buy a remote server from amercia of linux ubuntu 7.04 seerver  i get the control through ssh i transfer some files in root folder and go to terminal by putty and get login but i m trying to execute the file it is showing bash permission denaid i know that i have to give permission to the file to execute i can do it but in gui not in command line can you tell me the command that how to give permission to the file to execute
and
is there any way to use this server in gui by vnc

---

### Post by lgambett on 2008-01-16
**chmod a+x filename**
will give to all the users in the system the execute permission.
Check
**man chmod**
to know all of the possibilities of this command.

I think you should ask to the provider of the remote server;
1) If a GUI is available on the remote server (not sure of that)
2) if it is possible to install a VNC Server on it.

---

### Post by taimur on 2008-01-16
yeah it is possible to install but they said you have to do it by yourself but how or is there any dedicated service provider who will give gui linux ubuntu remotly

---

