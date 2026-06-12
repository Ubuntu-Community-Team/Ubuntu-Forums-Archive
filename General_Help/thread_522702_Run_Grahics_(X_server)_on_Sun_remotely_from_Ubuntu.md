---
title: "Run Grahics (X server) on Sun remotely from Ubuntu"
date: 2007-08-10
forum: General Help
---

### Post by skoufis on 2007-08-10
I am trying to connect remotely to a Sun workstation at school from home to run some graphical applications (circuit simulation tools).  Everything works fine on XP (Cygwin, Exceed) but in Ubuntu it cannot set the DISPLAY variable right...I think.  I do the following:

1. Activate the VPN client
2. Add remote Sun host with: xhost +<Sun hostname>
3. rlogin on Sun workstation (Solaris 9 running C-shell)
4. I set the DISPLAY variable: setenv DISPLAY <VPN client IP>:0.0
5. I try a graphical application like "nedit" or "matlab" and it cannot open the display for <VPN client IP>:0.0.


I appreciate any hints,
Mike

---

### Post by PaulFr on 2007-08-11
For the examples below, I assume your local machine is 192.168.100.3 and it is also the machine on which you run the VPN software. Also I assume the remote machine where you want to run nedit or matlab is 172.20.1.15 and the end of the VPN tunnel in that remote network is 172.20.1.31 (this is the internal IP address of the VPN gateway).

Here's what I needed to do to make it work:

1. You have to make sure that the machine where you want to run nedit or xterm or matlab knows how to direct packets that need to travel to your local machine. So there should be a default route to 192.168.100.0 with gateway as 172.20.1.31 on the machine (172.20.1.15) where you run nedit or matlab. **netstat -rn** to check. If you do not have that, you will probably need root / sudo access to set up this route.

2. Your X-server on your local machine should listen for TCP requests. To check if it is, I used the command **netstat -an|grep LISTEN|grep 6000**. Since it was not, I hunted in the /etc folder for the kdmrc file (I run kdm, the file was at /etc/kde3/kdm/kdmrc) and commented out the option **-nolisten tcp** and restarted the machine. If you are running gnome, you should be able to find a **DisallowTCP** option in /etc/gdm/gdm.conf.

3. Now I connected and tried to ping my local machine. This worked, but running **xterm** did not work, since I had not authorized the remote machine to connect. That was easy: **xhost +172.20.1.15** did the trick.

Hope this gives you some ideas.

---

### Post by skoufis on 2007-08-11
Thanks a lot...I will try that :)

---

