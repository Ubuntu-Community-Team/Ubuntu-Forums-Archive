---
title: "Inactivity suspend asks for password"
date: 2017-04-09
forum: General Help
---

### Post by frytek on 2017-04-09
I've got Lubuntu 16.04 on Dell Latitude E7470. I configured suspend while closing the lid and it works perfectly. It also works from logout/suspend menu -- the laptop suspends correctly and wakes up correctly (asking for a password to unlock - as configured). 

However,  when the system is supposed to suspend while inactive it will follow the procedure of dimming the screen, turning off the screen (both configured separately in the power manager)... but when the time comes to sudpend, the screen wakes and I get the password prompt. When I type it, i get the desktop with a bubble message saying something like: "GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: Operation not permitted".

I looked for this problem and it seems the reason are polkit or pam permissions. 

I found similar problem described for xubuntu here: [http://askubuntu.com/questions/627356/xubuntu-15-04-cannot-suspend-when-inactive](http://askubuntu.com/questions/627356/xubuntu-15-04-cannot-suspend-when-inactive)
One of the solution is: 

```
At the terminal, type:
xfconf-query -c xfce4-power-manager -lv
If the output of the above command doesn't contain the following line:
/xfce4-power-manager/inactivity-sleep-mode-on-battery   1
then, at the terminal type:
xfconf-query -c xfce4-power-manager -p /xfce4-power-manager/inactivity-sleep-mode-on-battery -n -t int -s 1
```

but there is no xfce power manager in Lubuntu. 

Can anyone tell me what to do?

---

