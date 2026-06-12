---
title: "Trouble running gnome-system-monitor"
date: 2008-02-14
forum: General Help
---

### Post by Hammer89 on 2008-02-14
Hello,

For some reason I'm not able to get gnome-system-monitor to run. I've tried launching it from the menu, panel applet, and from the terminal... all to no avail. When I attempt to run it from the terminal it displays this error:

> matthew@matthew-laptop:~$ gnome-system-monitor

** (gnome-system-monitor:1202): WARNING **: SELinux was found but is not enabled.

terminate called after throwing an instance of 'Glib::FileError'
Aborted (core dumped)

The only changes I've made to my system right before it happened were some updates from synaptic... which included a few kernel updates. Any assistance would be greatly appreciated. Thanks. :)

---

### Post by jan quark on 2008-02-14
it seems to be a bug
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/180087](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/180087)

try 
ctrl+alt+backspace
to restart the display, perhaps it helps for while

---

### Post by Hammer89 on 2008-02-14
Interesting... the problem would seem to somehow be related to firefox and my icon theme... I changed my icon theme and was able to open the system monitor, however it immediately caused firefox to freeze. It would appear to only be a problem when I have the process tab selected as well.

---

### Post by craigyjack on 2008-03-11
the firefox freezing isnt related to the gnome-system-monitor probably. firefox does not handle well when you change a gtk theme when its open. normally it'll freeze or crash, it always does that for me if firefox is open and i change a theme (sometimes i'tll unfreeze after a long while if it doesnt crash). this problem will prob be fixed with firefox 3 sicne its full gtk compatable now (i have firefox 3 beta, but havent changed my theme to test this problem).

I also got this bug with gnome-system-monitor, thats i came upon this thread - but i'd thought i'd reply just to clarify the firefox thing.
-Craig

---

