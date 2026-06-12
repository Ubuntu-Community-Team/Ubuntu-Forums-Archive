---
title: "[SOLVED] Install X11+Fluxbox through remote ssh??"
date: 2008-01-24
forum: General Help
---

### Post by ghandi69_ on 2008-01-24
Hello,

I have had, for the past several months, a perfectly working Ubuntu server install, console only installation meaning no window system or anything like that, and I use it as a web/ssh/samba server.

However, I have recently had the desire to make it an Urban Terror server as well.  In order to do this, I believe, I will need to install Fluxbox or some other lightweight window manager as well as x-window-system core and such.

Is there a way for me to be able to install this remotely through SSH, and then be able to login remote without ever hooking a monitor up to the server (or keyboard) for that matter?

---

### Post by tekreloaded on 2008-01-24
Hi,

Just a suggestion - you can probably install X11 + Fluxbox remotely using apt-get and aptitude e.g. just run aptitude, search for the X11 and Fluxbox packages you need and then install them.

But if you are not going to use a monitor or anything on the server then you don't REALLY need X11 on the server but you will probably have to install for dependencies.

Once you have install X11 on the server then you can run X11 programs by doing:

ssh -X user@server

and as long as you have a X server running on the client, you can just run any X11 program and it will be displayed locally...

Alternatively, you can do startx over SSH and then use VNC to connect and use fluxbox desktop...

---

### Post by ghandi69_ on 2008-01-24
Hey there, thanks for the help.

I have tried doing as you say, however, when I connect using ssh that way, and try to run a program that recquires a window ( say... xterm) I get this...

> xterm Xt error: Can't open display: 
xterm:  DISPLAY is not set


---

### Post by Nythain on 2008-01-26
dude, you are gonna have to go beyond a standard ssh connection to run a Desktop Environment or Window Manager...
You could, however, tunnel a VNC connection through ssh for security reasons, and connect to the machine via a VNC viewer (tightvnc is what i use) to launch a GUI that way.
google "ubuntu ssh vnc"
or search for "ssh vnc" on these forums for many different how to's on this subject.

but alas, ssh alone isnt gonna cut it, thats like trying to run Windows through telnet

Edit: Just realized i said exactly what Tek said... good advice there tek (sorry i didnt really read anything before the last problem post by poster :( )

---

### Post by ghandi69_ on 2008-01-29
Thanks guys, while it took a while to get it working, I am now successfully forwarding X11 programs from the server (to linux box's at least).

---

### Post by tekreloaded on 2008-02-03
:D
SSH X11 forwarding is great and I use it for lots of remote work.

Quote: (to linux box's at least)
Answer: To use X11 forwarding on windows, you can do the following:

1) Download XMing ([http://sourceforge.net/projects/xming](http://sourceforge.net/projects/xming)) onto your windows box and install.

2) Download PuTTY ([http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)) and either install on computer or on USB drive or whatever.

3) Start XMing server

4) Run PuTTY, select SSH, type the hostname into the box BUT DON'T CLICK OPEN!!!

5) In the tree on the left, choose SSH, then within that choose X11. Tick "Enable X11 Forwarding" and make sure "localhost:0" is entered in the location box and that MIT-Magic-Cookie-1 is selected.

6) Go back to the main (Session) screen and save the settings for the future.

7) Click connect and USE :D

(I think that's everything - tell me if I've missed something)

---

### Post by ghandi69_ on 2008-02-03
Hey, thanks for your continued help on the subject.

However, using Putty with those options does not seem to allow me to forward X11 to windows.

I get the following error.

X connection to localhost:10.0 broken

Now, I tried switching localhost:0 per your directions to localhost10:0, but I get same error.

Another thing, when I connect from a linux machine, I use -Y instead of -X to get it to work, which I guess bypasses some security measures.  I set the SSH- auth settings to bypass, but I get errors that way as well.

Thanks again for the help, and I'll keep trying some things.

---

