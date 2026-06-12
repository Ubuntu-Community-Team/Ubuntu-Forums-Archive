---
title: "no-permission user for ssh port forwarding?"
date: 2008-06-03
forum: General Help
---

### Post by PreviousN on 2008-06-03
I sometimes like to ssh home to forward port 80, since I have some web services that I like to have access to at school. The problem is that sometimes I need to leave the computer and I know that my friends will "mess with" my stuff. 

I want to set up a user that has NO privileges except for being able to forward ports. How can I do that? I prefer terminal commands, btw. 

Thx!

---

### Post by HalPomeranz on 2008-06-03
When you make the SSH connection back to your home computer, just use the following options (in addition to the other normal options on your command line): "-nNTx".  The "-n" option disables the standard input so nobody can type commands into your SSH session, the "-N" option disables the command channel completely thus preventing anything but port forwarding, the "-T" option disables pty allocation on the remote machine just to make doubly sure that the remote command channel won't work, and "-x" disables X11 forwarding.

Note that anybody who sits down at your computer while you're away can still use the port forwarding to browse whatever web site you've tunneled to.  So I still recommend you lock your screen when you step away from the computer.

---

### Post by jimv on 2008-06-03
Kick their asses.  Then it shouldn't be an issue.

---

