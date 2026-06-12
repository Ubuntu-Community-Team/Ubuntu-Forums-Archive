---
title: "Blank Login Screen (but I can see mouse pointer)."
date: 2020-04-09
forum: General Help
---

### Post by warren3 on 2020-04-09
Hi.


I've been using 19.10 since its release with no issues. The only issue I came across is that if the system logs you out and a period of time passes since log out I cannot use the login box and I have to change to tty2 and use 'shutdown -r now' to reboot the system.


I have done this a few times with no issue but when I did it last night after reboot I was greeted with a blank screen and a mouse pointer. After googling the issue I have tried:


>startx command (gives an error - see pic)


>sudo startx (gives a dbus error 'startx could not sync environment to dbus', but I have since read it is wrong to use sudo with startx).


>tried to delete .Xauthroity from home folder and reboot.


>systemctl restart lightdm.service


>systemctl restart sddm.service


Nothing has worked. I could do with some help.

---

