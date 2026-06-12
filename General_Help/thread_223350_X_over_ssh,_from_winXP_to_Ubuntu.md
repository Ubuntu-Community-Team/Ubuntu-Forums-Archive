---
title: "X over ssh, from winXP to Ubuntu ?"
date: 2006-07-26
forum: General Help
---

### Post by conza on 2006-07-26
hi,

i've been trying to find a useful guide for this, but been unable to... :(

what I want to achieve is the following:

from my winxp client, run x-window over a ssh connection to my Ubuntu pc. 

I've manage to get a ssh connection with putty to the ubuntu client, but it is only in "terminal mode", and I need the GUI... 

what do I need to do, on the winxp and the ubuntu machines to get this to work? or if anyone know a GOOD guide... i'm still a newbie when it comes to linux... :) 



thanks!

---

### Post by bensexson on 2006-07-26
You will need a X server for windows.  I use cygwin.  [http://www.cygwin.com/](http://www.cygwin.com/).  The install is pretty straight forward.  Then start X cygwin and ssh -X <other machine>.  This will redirect X back through to your Windows machine.

---

### Post by SeanHodges on 2006-07-26
Do you want the entire desktop, or just certain applications? X over SSH (such as what you're trying to do with putty) will allow you to run graphical applications remotely, but if you want an entire remote desktop (slower, but some people prefer everything in a single window) you'll be wanting rdesktop or x11vnc...

For X11 forwarding over SSH:

1. Download and install Cygwin [www.cygwin.com](www.cygwin.com) on the Windows PC
2. Set "X11Forwarding yes" in /etc/ssh/sshd_config of your Linux box
3. Restart SSH: "sudo /etc/init.d/ssh* restart"
4. On the Windows PC, type "ssh -Y 192.168.1.2" or whatever your Linux box IP is.
5. Test it by typeing "xclock" in the SSH terminal.

I dont have my machine in front of me here, if I missed anything out I'm sure someone will correct me ;)

Cheers,

Sean

EDIT: Sorry, didnt notice you're using Putty: instead of typing "ssh -Y...", load up Putty and make sure "X11 Forwarding" is enabled in the [Tunnels]("http://www4.gantep.edu.tr/putty-x11.jpg") tab

---

### Post by conza on 2006-07-27
thanks guys, will take a look at this during the weekend.. :)

i'm mostly interested in being able to run Firefox, not really in need of any other graphical application/window..

br,

conza

---

### Post by topgi on 2006-07-27
Try Ximing. It is much better than Cygwin to pursue your scope. Cygwin is more for run unix under windows. Ximing is just an Xserver, open source. I use it all the time to do exactly what you are doing.

---

### Post by Epskampie on 2008-01-20
The person above me meant [Xming](http://sourceforge.net/projects/xming)

---

