---
title: "VNC through ssh to view Desktop - Troubleshooting"
date: 2015-12-31
forum: General Help
---

### Post by chiques on 2015-12-31
I currently have a **remote**.ubunterserver which I am able to ssh into and start a x11vnc server from my** local**.ubuntuserver. The problem is when I try to use the recommended VNC desktop I receive an error: "No such host is known" (see below)



[IMG]http://oi68.tinypic.com/erwlnc.jpg[/IMG]


I have done this before in local networks but in this case remote.ubuntuserver is behind a commerical Cox Cable modem/router. I have port forwarded the ssh ports along with the ports 5900-5902 (not sure if this matters) but I still receive the error.

Any suggestions or logs I can look are appreciated.

---

### Post by chiques on 2015-12-31
I first log into ssh of the remote.ubuntuserver machine then I run this as sudo:

> sudo x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -usepw

just and fyi:
> ssh -t -L 5900:localhost:5900 remote.ubuntuserver 'x11vnc -localhost -display :0'

Does not work for me. I get the infamous ***"XOpenDisplay failed (:0)"*** error

---

### Post by steeldriver on 2015-12-31
If I'm reading your terminal output correctly, the x11vnc server is listening on port 590**2** not 5900 (corresponding to display :2) so if you are trying to use SSH tunnelling, you will need to tunnel that port instead

I don't recognize the particular VNC viewer you are using: however if it requires you to set up the tunnel manually, then almost certainly you should be pointing it at localhost:2 or localhost:5902 (or whatever port you tunnel the remote 5902 to, doesn't have to be 5902-->5902 although that makes things a little simpler)

---

### Post by chiques on 2016-01-01
> **steeldriver said:**
> If I'm reading your terminal output correctly, the x11vnc server is listening on port 590**2** not 5900 (corresponding to display :2) so if you are trying to use SSH tunnelling, you will need to tunnel that port instead

I don't recognize the particular VNC viewer you are using: however if it requires you to set up the tunnel manually, then almost certainly you should be pointing it at localhost:2 or localhost:5902 (or whatever port you tunnel the remote 5902 to, doesn't have to be 5902-->5902 although that makes things a little simpler)

Hello steeldriver,
You are correct, I kept killing and restarting the x11server (incorrectly) so it was incrementing the desktop ID during my screen captures. I am using RealVNC ([http://www.realvnc.com/](http://www.realvnc.com/)) and TightVNC viewers.

I attempted to log in again (BEHIND THE FIREWALL/ROUTER) and was able to VPN without any issues. It appears there are some ports on the router that need to be opened that I'm not aware of.


I launched my x11 server:

[IMG]http://i66.tinypic.com/20z1ci9.jpg[/IMG]


Then I connected with TightVNC
[IMG]http://i63.tinypic.com/118mvco.jpg[/IMG]

---

### Post by chiques on 2016-01-02
I scrapped the 'x11...' command approach and just ended up using this:
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-14-04) 

It worked the first time around.

---

