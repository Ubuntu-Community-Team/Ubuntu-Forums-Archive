---
title: "Use GUI on different machine then server"
date: 2015-12-08
forum: General Help
---

### Post by Cool_Javelin on 2015-12-08
I have Ubuntu Server 12.04 LTS (Lets call him MrServ) running some stuff, it is VERY stable, and I don't want to change it (much).

MrServ has no GUI, that is it is a CLI interface only.

I have read I can have a GUI environment on a different machine elsewhere on my network. Is this true?

Can I run a program in Windows that will be the graphics environment (Gnome maybe?) and run commands on MrServ? What do I have to do to MrServ?

Or, I have a virtual machine (in Windows) running an Ubuntu desktop (Lets call this machine MsLooker.) Can I make that desktop interface to MrServ rather then MsLooker?

Even better, on MsLooker, can I have two Gnome environments run simultaneously and switch between them similar to switching the TTY screens using the ALT-Fn keys? 
Or run a "Window within a window" on MsLooker doing stuff on MrServ?

I think this concept has something to do with X, but I am unclear how it all works.

Any Help?

thanks, Mark.

---

### Post by ian-weisser on 2015-12-08
> **Cool_Javelin said:**
> I have read I can have a GUI environment on a different machine elsewhere on my network. Is this true?
Yes.
Your network must have plenty of capacity.
Your hardware must be powerful enough.
It's not trivial to set up.

See VNC: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
There is also RDP, another way of doing the same thing, but the wiki page for it is rather lacking.

---

### Post by HermanAB on 2015-12-09
Assuming that the server has sshd installed and running and has gedit installed, with no X server running:

Then from another machine:
$ ssh -X -C -c blowfish user@serveraddress "gedit filename"

and the remote gedit will pop up transparently on the local machine desktop.

---

