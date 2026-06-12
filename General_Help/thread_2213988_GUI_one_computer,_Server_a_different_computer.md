---
title: "GUI one computer, Server a different computer"
date: 2014-03-29
forum: General Help
---

### Post by Cool_Javelin on 2014-03-29
I have two Ubuntu servers running 12.04.2 LTS and I would like to connect a GUI (Gnome for example) from a third computer.

This third computer will be running a virtual Box with a Ubuntu 10.10 desktop install with Gnome.

One server is wired to my router, the other will be wireless, but I think that won't matter.

Both servers are running now as is my virtual box desktop.

Can this be done? How do I do it?

Thanks. Mark.

---

### Post by The Cog on 2014-03-29
Not easily. Ubuntu server doesn't have a GUI by default. You can install one, but to be honest, I don't think you really need it.

The most common thing to do when administering a server is to copy/move/edit files. The best way to do this is to mount the server's filesystem and use you local file manager to do that stuff. I think you can open a remote machine in nautilus file manager with something like this in the address bar:
```
sftp://username:1.2.3.4/
```
And then you can edit the files with right-click as though they are local. 

Unless there is a graphical app that you want to run on the server (I have occasionally wanted to run wireshark on a server for instance). Installing a graphical app on the server will install an awful lot of GUI library packages. You can then run the graphical app remotely with something like this command:
ssh -X useranme@1.2.3.4 wireshark
which will run wireshark on the server but with the GUI interface projected onto your desktop over the SSH connection.

---

