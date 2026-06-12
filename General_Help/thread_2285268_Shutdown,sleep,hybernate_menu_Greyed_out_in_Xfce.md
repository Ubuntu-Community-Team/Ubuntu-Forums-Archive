---
title: "Shutdown,sleep,hybernate menu Greyed out in Xfce"
date: 2015-07-04
forum: General Help
---

### Post by Nargren on 2015-07-04
Hi,

I was tweaking my laptop trying different themes and icon sets, login managers and similar the other day. After some time I realized that the shutdown, sleep etc. buttons are greyed out in the menu and I can't access them.
[IMG]http://pcgeeks.bugs3.com/wp-content/uploads/2015/07/Screenshot-040715-145510.png[/IMG]

Pressing ALT+F4 gives me a similar menu that I have been happily using so far, but it would be nice to have the original menu back as well.

I'm guessing either with my login manager or maybe the display manager?

Ubuntu 12.04.5 LTS | XFCE4

```
dpkg -l | grep -i 'Display Manager\|Login Manager' | awk '$2 !~ /^lib/'
ii  gdm                                      3.0.4-0ubuntu15.3                       GNOME Display Manager
ii  lightdm                                  1.2.3-0ubuntu2.7                        Display Manager
ii  slim                                     1.3.2-1                                 desktop-independent graphical login manager for X11

```


Could I get some hints where should I look or what could be wrong? Help would be appreciated! Thanks!

---

### Post by Nargren on 2015-07-10
Anything from anyone?

---

### Post by Toz on 2015-07-13
You have 3 Display Managers installed. Which one is the active one?

---

### Post by Nargren on 2015-07-25
lightdm, I have just removed everything else to avoid any possible interference. The situation is still the same however.

---

### Post by Toz on 2015-07-26
While trying the other 2 display managers, did you create any x init files? Like ~/.xinitrc? Or change system X startup files?

---

