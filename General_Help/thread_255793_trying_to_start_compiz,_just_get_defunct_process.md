---
title: "trying to start compiz, just get defunct process"
date: 2006-09-12
forum: General Help
---

### Post by themoebius on 2006-09-12
I'm using 0.0.13-quinn25, I'm running nvidia, AMD64. when I start the compiz session I just get regular gnome

zac@moebius:~$ ps -ef |grep compiz
zac       9374  9328  0 18:45 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /home/zac/compiz.sh
zac       9378     1  0 18:45 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /home/zac/compiz.sh
zac       9380  9328  0 18:45 ?        00:00:00 [compiz] <defunct>


zac@moebius:~$ ps -ef |grep Xgl
root      9317  9312  4 18:44 ?        00:01:15 /usr/bin/Xgl :0 :0 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer -kb -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      9318  9317  0 18:44 tty7     00:00:03 /usr/bin/Xorg vt7 -auth /tmp/.Xgl-auth-fMP2cb -nolisten tcp :93 -terminate

theres nothing containing the word compiz in /var/log

---

### Post by meborc on 2006-09-12
you should try to ask in one of the compiz/xgl threads in tips/trick section... you will probably find an answer there, or get better feedback :wink: 

good luck

---

### Post by Ramses de Norre on 2006-09-12
Have you tried starting compiz with ```
compiz-start
```

---

