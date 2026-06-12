---
title: "Multiple Users/Desktops Logged in at the same time"
date: 2013-01-29
forum: General Help
---

### Post by Litzner on 2013-01-29
Is it possible in Lubuntu/Ubuntu to have the computer screen/monitor to be logged in as one user, and when I remote in, I remote in as a completely different user/session/desktop, not interrupting the user on the screen/monitor?

Is this hard to setup or something standard/simple?

---

### Post by kanikilu on 2013-01-29
How are you logging in remotely? If VNC, then no, I don't think you'll be able to have multiple separate X sessions. For that, here at work I use FreeNX:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

Don't let the length of the documentation turn you off, though - I want to say when I installed it last (although it's been a couple years), it was as simple as adding the PPA repo and then installing it with apt-get. 

That's the setup on the server. From the client computer, it just requires the "NoMachine NX Client". It can be downloaded here:

[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

---

### Post by SeijiSensei on 2013-01-29
If you're comfortable with the command line, just use SSH.  If there are specific graphical applications you'd like to run, you can log in with "ssh -X you@remote_server" then launch the application from the command line.  Give it a try.  When you get the prompt from the remote server type something like "firefox &". (The ampersand "&" tells the server to launch firefox and run it in the background.  You'll get the prompt back after it launches.) You should now see Firefox appear on your local screen.  Unless you need to see the entire remote desktop, this is a nice lightweight solution that uses the native networking features in X, the windowing system for Unix.

---

### Post by omeomi on 2013-01-29
If you're using SSH to login remotely than this will work the way you want by default. Each time you login you will start a new session that is independent of other sessions (even using the same username).

---

### Post by Litzner on 2013-01-30
No I will not be using SSH when I remote in to this box. I will most often be remoteing in to manage different downloads I run when I am away from home, and would require the use of the desktop.

On FreeNX it says they are having problems resuming sessions, does that mean re-connecting to a session you have left active?

---

### Post by omeomi on 2013-01-30
Using Screen you can keep sessions active and log into those sessions remotely. This works over ssh and you can use the desktop over ssh as well if you do the following.
```
ssh -X user@remote-address
nautilus &
```

This will start up the nautilus desktop on the remote computer. Look at the Screen documentation to see how that fits into these commands, I believe you have to add a port number or similar to the ssh command.

---

