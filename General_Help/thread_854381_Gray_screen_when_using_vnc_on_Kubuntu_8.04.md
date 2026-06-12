---
title: "Gray screen when using vnc on Kubuntu 8.04"
date: 2008-07-09
forum: General Help
---

### Post by erezz on 2008-07-09
Hi,

I a kubuntu newbie and I have a question about vnc. Whenever I connect from WIN-XP via vnc, I get a gray screen. Here's my xstartup script from ~/.vnc:

#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc
exec kde-menu

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
twm &

I just run vncserver like this:

[email]erez.zilber@erez-lx:~/.vnc[/email]$ vncserver

New 'X' desktop is erez-lx:1

Starting applications specified in /home1/erez.zilber/.vnc/xstartup
Log file is /home1/erez.zilber/.vnc/erez-lx:1.log

I saw that people are talking about /etc/vnc.conf. I don't have such file.

Any idea?

Thanks,
Erez

---

### Post by nikgare on 2008-07-10
Have you waited long enough?
SOmetimes when I use vnc to a winxp machine, I have to wait about 20secs to a minute untill the display starts displaying thing?

---

