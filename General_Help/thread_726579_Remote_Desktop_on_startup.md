---
title: "Remote Desktop on startup?"
date: 2008-03-16
forum: General Help
---

### Post by keninem on 2008-03-16
Hi all..new to Ubuntu, but have been using Linux for a few years..

I have a laptop that the screen has died on, and wanted to be able to remotely access Ubuntu on it.. I installed Ubuntu desktop and am able to get the Remote Desktop working, but it requires a login to the system first..IE if I were to lose power, I would have to hook a monitor up to it and login, and then would be able to remotely connect.

I tried installing tightvnc, with no success..it gave me display errors..I can go back to a vnc install if that's what's recommended, but it seems like there should be a way to add the Remote Desktop to a startup script..any help is appreciated!

Thanks!

---

### Post by HermanAB on 2008-03-16
Don't use VNC.  Install OpenSSH-Server.  Millions of headless servers world-wide are managed through SSH:

ssh -c blowfish -C -X [email]user@ip.add.re.ss[/email]

Once logged in you can run any program including X programs, or even the taskbar if you are feeling clicky and cannot remember the name of the program to run:

ssh -c blowfish -C -X [email]user@ip.add.re.ss[/email] "gedit /etc/fstab"
ssh -c blowfish -C -X [email]user@ip.add.re.ss[/email] kicker
ssh -c blowfish -C -X [email]user@ip.add.re.ss[/email] gnome-panel

and so on.

Of course, you can change the default settings in /etc/ssh/sshd_config so you need not type all those parameters.

Cheers,

Herman

---

### Post by keninem on 2008-03-17
Thanks for the reply Herman, but my only other machine is a Windows Vista box, so while I will be doing most of my remoteing through ssh command line, I do have some need to access the linux desktop from that Vista box..

---

### Post by HermanAB on 2008-03-17
Use XMing and PuTTY, or Cygwin with OpenSSH:
[http://sourceforge.net/projects/xming](http://sourceforge.net/projects/xming)
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

Cheers,

H.

---

### Post by bodhi.zazen on 2008-03-17
What problem are you having with VNC ?

This link reviews how to configure it :

[uwiki]VNCOverSSH[/uwiki]

You do no need to use ssh if you do not want.

@HermanAB : Or start a new Virtual X session (on say Ctrl-Alt-F8) and forward the whole desktop;)

---

