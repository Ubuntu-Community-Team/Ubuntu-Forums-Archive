---
title: "VNC Raspberry pi Ubuntu connection refused after Reboot"
date: 2022-02-20
forum: General Help
---

### Post by jf-pt on 2022-02-20
Good Morning,
I have a Raspberry pi 4 8GB ram version, where I installed Ubuntu 21.10 64bit version.
In order to avoid having to carry a screen while traveling, I started using VNC Viewer on my personal computer. So in "settings"->"Sharing"->"Screen Sharing" I put the following settings:

[https://i.postimg.cc/cH0wsnRZ/1.jpg](https://i.postimg.cc/cH0wsnRZ/1.jpg)

I noticed that every time I rebooted the raspberry pi, the "Screen Sharing" password was "forgotten". After some research, [https://askubuntu.com/questions/1296932/screen-sharing-in-unusable-state-after-rebooting](https://askubuntu.com/questions/1296932/screen-sharing-in-unusable-state-after-rebooting), I found out that there is a bug in Ubuntu that for each reboot the password for "Screen Sharing" was cleared. The alternative to solve this situation would be to go to the "Passwords and Keys" application in login, change the password to a blank password (of course it's not secure at all, but at least it solved it):
[https://i.postimg.cc/cCVJLppY/2.jpg](https://i.postimg.cc/cCVJLppY/2.jpg)


In summary now every time I reboot these "Screen sharing" settings are saved.However, I am now being faced with another problem:


If I reboot the Raspberry pi but with the hdmi cable connected directly to an external monitor, I can from my personal computer connect to the raspberry pi via VNC Viewer.


On the other hand, if the Raspberry pi is not connected to an external monitor by the hdmi cable, at the end of a reboot, when I try to connect to the raspberry pi via VNC Viewer, I am confronted with the following message:
"Connection refused by the computer"


What I am finding strange is that if I next reboot with an external screen, I find that the "Screen Sharing" settings, remain intact.


Given this situation, I would like to know if anyone else has been confronted with this situation and if there is a solution.


Thank you very much for your attention.

[https://postimg.cc/CZrz7dr6](https://postimg.cc/CZrz7dr6)

---

### Post by TheFu on 2022-02-20
Don't use VNC.
Use x2go.  x2go is based on the NX protocol that leverages existing ssh authentication and has many other features. Best of all, there can be 20+ concurrent users on the same system and we can choose to connect to an existing session (owned by our ssh user) or create a new session.  Also, x2go is 2-3x faster than rdp or vnc.

I really wish they'd stop showing VNC as the remote desktop method. It makes things hard for so many people when it just isn't necessary.

The only trick for x2go is not to use Gnome3+ as the DE.  Using anything else - XFCE, KDE, LXQt, LXDE, or any pure WM you like.
I've used x2go to remote home from 5 continents, once over a shared ISDN connect at the edge of Patagonia.  Worked fine - I just reduced the connection speed that x2go expected for the connection and it increased the compression. Good stuff.

If you are on the same LAN, there are faster, more convenience answers via remote X11 methods.  I use this all day, every day.  Right now, I'm running this web browser on a different machine than where I'm typing or have any hardware connected, for example. I do the same for email and most 'desktop' productivity applications. Those all run on another machine, not the 1 I actually sit behind and type onto.

---

