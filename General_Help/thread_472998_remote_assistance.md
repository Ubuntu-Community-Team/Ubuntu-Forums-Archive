---
title: "remote assistance"
date: 2007-06-13
forum: General Help
---

### Post by celticbhoy on 2007-06-13
Is there an equivalent to windows remote assistance with feisty on both PC's

---

### Post by DjKritical on 2007-06-13
Ubuntu has Remote Desktop Software built into itself called "Vino"... it's easy to turn on, system -> preferences -> remote desktop.  This will allow you to open your computer up for remote control but only when you are logged in.

The client in Ubuntu is located in Applications -> Internet -> Terminal Services Client (Make sure you choose VNC as the connection type).

If you want to connect from a Windows machine you will need to download a VNC client, try [http://www.tightvnc.com]("http://www.tightvnc.com/") or [http://www.realvnc.com]("http://www.realvnc.com") or [http://www.uvnc.com]("http://www.uvnc.com")

Now this solution will only work if you are actually logged into Gnome, if you've got major problems this wont help you..

There is also sshd which is basically an ssh server...

sudo apt-get install ssh

To connect to the ssh server in linux type -> ssh username@hostname

To connect to the ssh server in windows download putty -> [http://www.putty.nl]("http://www.putty.nl")

Good luck

---

### Post by celticbhoy on 2007-06-13
Just to check I got all info I need when the computer to give control sets up with your first line, the computer name listed is then used by the controlling computer via T.S.C. to gain control ??

---

### Post by DjKritical on 2007-06-13
It really depends on what you are doing...

Basic answer: yes

---

### Post by celticbhoy on 2007-06-13
Really just looking for an easy way to help a friend who I have just put onto feisty. So as I say just like the windows remote assistance.

thanx for the help.

---

### Post by DjKritical on 2007-06-13
Well the important information needed would be things like:

What operating system are you connecting from?
Can your friend log into Gnome?

If you're connecting from Ubuntu to Ubuntu then use Vino/T.S.C...

Get your friend to go to [http://www.whatismyip.com]("http://www.whatismyip.com") to get his IP Address.

If he is behind a router he will need to configure port forwarding for tcp port 5900 (If he were doing windows remote assistance it would be port 3389)

Good luck :D

---

### Post by celticbhoy on 2007-06-13
Sorry but just to check again .....

in T.S.C. -> Logon Settings, the computer name is my friends I.P. address, or the computer name given on his vino preference screen ???

---

