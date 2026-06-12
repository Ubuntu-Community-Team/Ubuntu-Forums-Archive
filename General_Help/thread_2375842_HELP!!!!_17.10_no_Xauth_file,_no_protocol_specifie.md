---
title: "HELP!!!! 17.10 no Xauth file, no protocol specified, cannot open display"
date: 2017-10-27
forum: General Help
---

### Post by Weedoobs on 2017-10-27
I don't know now to fix this...I've been searching for hours and  trying and nothing. I have Ubuntu 17.10 fresh install, After i run "sudo  apt-get install gksu" i run into this problem.
Every time i try to run something from the terminal now, i get "No  protocol specified" and i can't open anything. Programs also don't open  from dash (half don't even show up) I would double click on something,  enter my password and no errors or anything it just won't start.
Single user, i restarted many times and 
 /etc/ssh/sshd_config
X11Forwarding yes

How do i fix it?

I also don't have a Xauthority file anywhere? Or atleast i didn't find any.

root@GlaDoS:/home/weedoobs# touch /root/.Xauthority
root@GlaDoS:/home/weedoobs# ps aux | grep Xorg
root      3908  0.0  0.0  22672  1072 pts/0    S+   21:33   0:00 grep --color=auto Xorg
root@GlaDoS:/home/weedoobs#

---

### Post by TheFu on 2017-10-28
17.10 doesn't use X11 by default. It uses Wayland which doesn't support remote X11 applications and some applications (like screen recorders) don't support wayland.
I understand there is a fallback X11 mode that is selected pre-login - just click the "gear".  [https://itsfoss.com/switch-xorg-wayland/](https://itsfoss.com/switch-xorg-wayland/)

---

