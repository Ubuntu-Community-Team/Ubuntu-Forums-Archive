---
title: "The terminal doesn't work properly"
date: 2014-09-26
forum: General Help
---

### Post by lucythedemon on 2014-09-26
Hey, I' ve been trying to learn to use the terminal and then this happened. I recently installed Ubuntu 14.04 LTS but I had this problem already before that.


When I execute files from the terminal, it shows for example this in the case of clementine:

```
14:25:23.986 WARN unknown QDBusConnection: name 'org.freedesktop.UDisks' had owner '' but we thought it was ':1.76' 
14:25:56.037 DEBUG unknown "sni-qt/2702" INFO 14:25:56.037 void StatusNotifierItem::slotAboutToShow() Adding an "Activate" entry to the StatusNotifierItem context menu

```

Then the terminal doesn't take any new commands or show the text username@pc:~$.


With rythmbox it says this: 
```
(rhythmbox:2571): Gtk-CRITICAL **: gtk_css_provider_load_from_path: assertion 'path != NULL' failed

(rhythmbox:2571): GLib-GObject-CRITICAL **: object SoupServer 0x17bc1c0 finalized while still in-construction

(rhythmbox:2571): GLib-GObject-CRITICAL **: Custom constructor for class SoupServer returned NULL (which is invalid). Please use GInitable instead.


```



Thank you for your help!

---

### Post by Lars Noodén on 2014-09-26
It looks like the terminal is busy running the program (rhythmbox) and showing you the output from that program.  It will be unavailable for anything else until that program finishes running.  Try quitting the program and you will see the shell prompt return. 

If you want to run a program in the background try launching it like this:

```

rhythmbox &

```

That will launch the program and drop it to the background immediately.  You will still see the text output from the program but your shell will still be available for interaction.

---

### Post by lucythedemon on 2014-09-26
Thanks,  this helped.

---

### Post by Lars Noodén on 2014-09-27
There are also pages here and there written about job control, if you'd like to know more about foreground and background tasks and so on.  Not all are that clear or even pleasant to read, but this one seems ok:

[http://www.cyberciti.biz/howto/unix-linux-job-control-command-examples-for-bash-ksh-shell/](http://www.cyberciti.biz/howto/unix-linux-job-control-command-examples-for-bash-ksh-shell/)

About Terminal program, you can make a new window with another shell pressing ctrl-alt-T again or ctrl-shift-N, or a open new tab within that window by pressing ctrl-shift-T  You can have as many open as you like.

---

