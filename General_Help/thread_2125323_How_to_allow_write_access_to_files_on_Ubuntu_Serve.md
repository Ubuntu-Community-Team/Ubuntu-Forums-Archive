---
title: "How to allow write access to files on Ubuntu Server so I can use Bluefish on Desktop"
date: 2013-03-13
forum: General Help
---

### Post by psyllex on 2013-03-13
I'm trying to do some web dev stuff with files on my Ubuntu Server.  I typically just use vi or emacs, secure shell into it and then make changes.  But I'd like to use Bluefish or Netbeans as a HTML editor, but when I remote connect into the files from my Ubuntu Desktop, I can't save the files to my server.  I use Ubuntu (Desktop)->Connect to Server -> the type is SSH.  Which should essentially be the same thing as ssh username@myserverIP in the terminal.   Do I need to sign in as root or something or is there a better way to do this?  

Additionally, really love notepad...alas it is not on Linux...could I possible use a Windows VM to connect remote to the Ubuntu Server and be allowed write access to files?  

Thanks in advance!  

By the way I'm running Ubuntu 12.04 LTS for both the Desktop and Server.

---

### Post by Mr. Shannon on 2013-03-13
Can you confirm that you can edit and save the file with ssh and vi/emacs.  It sounds like a permissions issue.  You could also use X forwarding, depending on the connection speed, but the way you are trying should work.  In Ubutnu you should never have to sign in as root.  And you should have root login disabled in /etc/ssh/sshd_config on the server.

---

### Post by papibe on 2013-03-13
Hi psyllex.

Are you connecting to the same remote user on both connections (terminal ssh and nautilus' connect to server)?

Regards.

---

### Post by psyllex on 2013-03-13
Actually it was a simple permissions issue. Even when I SSH by way of the terminal I have to **sudo emacs someFile **in order to change it.  So I just logged in as root in the Nautilus' connect to server and it works awesome now.  Still wish they made Notepad++ for Linux.

---

