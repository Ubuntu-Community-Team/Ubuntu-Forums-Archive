---
title: "Xubuntu desktop over ssh-CygwinX"
date: 2007-02-26
forum: General Help
---

### Post by sugna on 2007-02-26
Using Cygwin/X on Windows XP, I've managed to login to my Xubuntu box via an ssh X terminal.  I can remotely run graphical programs such as Firefox and Thunar so that they render nicely on my Windows PC.  Yippee!

However, what I would really like to do is run the whole xfce desktop so I can access all the panels and operate multiple windows as if I was using the normal Xubuntu desktop.

The command 'xfdesktop' will give me the desktop background and some right-click functionality, but no panels and menus.  Is there a simple way of running the whole xfce desktop from the x terminal?  

I know that remote desktopping can be done with VNC (and even with VNC tunneled through ssh), but I want to do it just with ssh and Cygwin/X if that is possible.  I also managed to do a remote desktop with XDMCP a while back, but if I could do it just with ssh that would be even better.

Thanks.

---

### Post by sugna on 2007-02-26
I think I've got it working.

The command "startxfce4" launched the desktop plus the top and bottom panels in three separate windows.  (Anyone know if they can be integrated or attached to behave as one?).

But then I realised that the xfce desktop can be set up so that the system menu is accessible via a right-click, so the panels are not really essential for basic desktop functionality.  So the 'xfdesktop' command is adequate if you can live without the panels.

---

### Post by ahmatti on 2007-03-17
Hi!
That sounds like a good idea! I will give it a try :)  You just gotta love X-forwarding!

---

### Post by thefox1959 on 2007-12-04
How do you start ssh-CygwinX anyway on XP? I installed Cygwin, but I can not find ssh.

Thanks in advance.

Greetings Paul

---

### Post by sugna on 2007-12-04
Umm, it was a long time ago, and I haven't dabbled in it since, but I seem to remember running ssh from the simulated (Cygwin) terminal, rather as an exe or bat file directly from Windows.

The command was something very simple, like "ssh username@ipaddress (or computername)".  There must be some instructions around somewhere because I don't remember having much trouble figuring it out.

Of course the other problem could be that you haven't installed the right components of Cygwin ... there are hundreds of them, and you've got to tick the right ones during installation.

Hope that helps ... like I said it was a while a go.

---

### Post by bodhi.zazen on 2007-12-04
> **thefox1959 said:**
> How do you start ssh-CygwinX anyway on XP? I installed Cygwin, but I can not find ssh.

Thanks in advance.

Greetings Paul

To be honest, you may have better luck with VNC and putty.

putty : [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

vnc : [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

vnc over ssh (putty) : [https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

But to answer your question, you need to install ssh on Cygwin, I think it is called open-ssh and it will install both a server and client. Then read how to start an X server (Xwin) and look at the options ...

---

