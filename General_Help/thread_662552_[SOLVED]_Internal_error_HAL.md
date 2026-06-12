---
title: "[SOLVED] Internal error: HAL"
date: 2008-01-09
forum: General Help
---

### Post by Mathijsken on 2008-01-09
Hello folks!
(I know there are some other threads with exactly the same problem, but I cannot get this one fixed.)

So when I try to login Gnome, it takes a lot of time before it actually finishes (wasn't like that before) and after that I get an error stating the wel known "Internal Error: Could not initialise HAL" - message.
I looked inside my /etc/rcX.d/ dirs to see if the HAL file was pressent, and yes it is there.

The systems log files don't tell me much more then that there seems to be something wrong with dbus and most likely that is the reason why HAL won't start.
Other daemons like, gnome-keyring-daemon and dhcpd daemons are also not started, or not functioning. (I quote these, because I use them for connecting to my VPN)

Everything can be easily resloved by restarting the dbus daemon, as this on also restart the HAL daemon and everything else.

So basicly my question is:** WHY WON'T DBUS START???**
It did before... I had no updates (except for a tomboy patch??) whatsoever... I didn't mess with my systems config...

If anyone has an idea where I should look for an answer, or even better if you have an answer, help me out please.
thanks!
Mathijs

---

### Post by Mathijsken on 2008-01-09
Okay I sort of repaired it myself

What I did was:
1 downgrade HAL to a feisty version (using feisty-baskports, I am using Gutsy)
2 reboot & enjoy the fact the HAL-error message is gone
3 upgrade back to the Gutsy HAL version
4 another reboot & still enjoy the fact the HAL-error message is gone, but notice dhcdbd is not running, so remove & re-add dhcbdb from startup using: 
```

sudo update-rc.d -f dhcdbd remove
sudo update-rc.d dhcdbd defaults

```
5 reboot again and enjoy the fact **EVERYTHING WORKS AGAIN!**

As far as I can tell, something (me?) screwed up the startup sequence of HAL and DBUS.
Anyway, I'm a happy user again...

greetz,
Mathijs

---

### Post by MrJokester on 2008-03-06
just reinstal hal and it must work like it usual
use this comand
```
sudo apt-get --reinstall install hal
```
and restart your mashin whit CTRL+ALT+BACKSPACE
after do this
start nautilus as a root
go to /etc/ look for the folder rc2.d rename s12hal to s13hal, or S50dbus to S12dbus.
then
```
sudo gedit /etc/init.d/rc
```
and change this line 
"CONCURRENCY=shell"
to "CONCURRENCY=none"
save it and thats it

---

