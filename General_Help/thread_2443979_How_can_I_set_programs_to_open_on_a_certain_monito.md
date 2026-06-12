---
title: "How can I set programs to open on a certain monitor?"
date: 2020-05-22
forum: General Help
---

### Post by victor47 on 2020-05-22
Hello everyone! I hope everyone's day is going alright!

I'm still trudging along the Linux learning curve, and I've come across a bit of a tedious issue.

I'm currently using ***Ubuntu Budgie 20.04LTS*** along with 2 monitors. Everything is great with one exception. If I move programs from monitor to monitor, no matter where I close and or resize. If I try reopening a certain program. In this case Celluloid. It'll ALWAYS open on the main screen.

However I've been trying to make it open on the second monitor. Is there a proper I can set applications to open on certain monitors?

I've searched for this solution, however the ones I found within Stack-overflow did not really help and the ones that do seem to be solutions are very terminal intensive. So I was wondering if there is a more noob friendly way to set this functionality.

Thank you in advance for any tips, tricks and overall instructions your masters can give.

Vic.

---

### Post by TheFu on 2020-05-23
Look up what the WM, Window Manager, supports.

For example, FVWM supports exact placement of each window if you like that.  No idea about other WMs.  Window placement is a WM function/responsibility.

The manpage for it seems useful: [http://manpages.ubuntu.com/manpages/bionic/man1/budgie-wm.1.html](http://manpages.ubuntu.com/manpages/bionic/man1/budgie-wm.1.html)
Sadly, they seem to have decided that man was to hard and use info format instead.  **info budgie-wm** hopefully has more details. I don't use budgie, so cannot see that information.

---

### Post by dragonfly41 on 2020-05-23
Possibly try [x-tile]("https://www.giuspen.com/x-tile/").

---

### Post by victor47 on 2020-05-23
Thank you for explaining! I'll do more research!

---

### Post by victor47 on 2020-05-23
> **TheFu said:**
> Look up what the WM, Window Manager, supports.

For example, FVWM supports exact placement of each window if you like that.  No idea about other WMs.  Window placement is a WM function/responsibility.

The manpage for it seems useful: [http://manpages.ubuntu.com/manpages/bionic/man1/budgie-wm.1.html](http://manpages.ubuntu.com/manpages/bionic/man1/budgie-wm.1.html)
Sadly, they seem to have decided that man was to hard and use info format instead.  **info budgie-wm** hopefully has more details. I don't use budgie, so cannot see that information.

What WM do you use? @TheFu

---

### Post by TheFu on 2020-05-23
fvwm. No DE.  Configuration is all text files.  [https://opensource.com/article/19/12/fvwm-linux-desktop](https://opensource.com/article/19/12/fvwm-linux-desktop)
I don't use menus.

Some desktop screenshots: [http://fvwm.sourceforge.net/screenshots/desktops/index.php?num=50](http://fvwm.sourceforge.net/screenshots/desktops/index.php?num=50)

---

### Post by kneutron on 2020-05-29
' wmctrl ' may help, I use it to switch to virtual desktop 3 and start virtualbox: [FONT=Menlo]alias vb='wmctrl -s 2; virtualbox &'[/FONT]

--Also you might try writing a bash script that launches the program with a -geometry parameter.  Setup the window where you want and run ' xwininfo ' from an xterm then click your program window, it will tell you the current geometry for it.

---

