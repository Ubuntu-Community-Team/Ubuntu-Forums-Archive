---
title: "Remote Administration"
date: 2008-01-24
forum: General Help
---

### Post by jessiejames on 2008-01-24
Good day to everyone,

I have some questions and need help for a particular application.

I have installed Kubuntu 7.1 at my home and I need to remotely administer my other computers. Apparently, my remote computers has PCAnywhere installed software and running at windows XP.

1. My question is, can we install PCAnyWhere at kubutu so I can access my remote computers with installed PCAnywhere running at Windows XP?

2. Or do we have any software for kubuntu that can access my other computers running at windowsxp?

3..What can we do to solve this problem?

Thank you very much as I shall await your help.

---

### Post by p_quarles on 2008-01-24
Haven't heard of PCAnywhere, but I'm guessing it's Windows-only. The standard cross-platform remote administration tool is SSH. You can install an SSH server on the Kubuntu machine by searching for the package called "openssh-server." For Windows, you will need to install an SSH client, such as [PuTTY]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/"). 

By default, SSH is a command line protocol. If you want to be able to access the GUI tools for administration, you have to enable "X forwarding." This is easy to do from Linux, but slightly more complicated for Windows: you will need to install an X server on XP. I haven't done this, so can't suggest the best way of going about it, but I do know that the most popular tool to use is [Cygwin]("http://www.cygwin.com/").

X server, if you're not sure what that means, is the bottom-most layer of Linux's graphical interface.

---

### Post by Mithrilhall on 2008-01-24
I use ssh, x11vnc and hamachi.

[https://secure.logmein.com/products/hamachi/vpn.asp?lang=en](https://secure.logmein.com/products/hamachi/vpn.asp?lang=en)

---

