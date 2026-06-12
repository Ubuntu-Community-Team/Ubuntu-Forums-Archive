---
title: "[SOLVED] Firefox keeps closing"
date: 2008-04-14
forum: General Help
---

### Post by carterrocks on 2008-04-14
It just keeps doing it and its getting annoying, i downloaded epiphany and it keeps doing it aswell!  Could someone help?

---

### Post by xaenyx on 2008-04-14
What version of ubuntu and firefox?  Are there any websites doing it in particular?

I've had trouble loading a lot of ajax-heavy websites (e.g. digg) in tabs in firefox 2, but this seemed mostly solved by upgrading to firefox 3.  Try disabling javascript and see if things work that way.

---

### Post by civic_si on 2008-04-14
Check your log files it should have a reason in there why its closing. Post the log file when you find it.

---

### Post by kellemes on 2008-04-14
> **carterrocks said:**
> It just keeps doing it and its getting annoying, i downloaded epiphany and it keeps doing it aswell!  Could someone help?

Run "firefox" from a terminal window and watch the terminal output when it crashes.

---

### Post by carterrocks on 2008-04-15
> **xaenyx said:**
> What version of ubuntu and firefox?  Are there any websites doing it in particular?

I've had trouble loading a lot of ajax-heavy websites (e.g. digg) in tabs in firefox 2, but this seemed mostly solved by upgrading to firefox 3.  Try disabling javascript and see if things work that way.

running the new beta in hardy heron and how do i post log files?  And I will post what the terminal says when it crashes

---

### Post by carterrocks on 2008-04-15
> **kellemes said:**
> Run "firefox" from a terminal window and watch the terminal output when it crashes.

Okay i got this....

```
mark@mark-desktop:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14491): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault (core dumped)
```

---

### Post by kellemes on 2008-04-15
A little googling suggests to remove "gtk-qt-engine" since this package may be the troublemaker..
Never hurts to try ;-)
```
sudo apt-get remove gtk-qt-engine
```

---

### Post by carterrocks on 2008-04-15
> **kellemes said:**
> A little googling suggests to remove "gtk-qt-engine" since this package may be the troublemaker..
Never hurts to try ;-)
```
sudo apt-get remove gtk-qt-engine
```

I used the command but the terminal says it isn't installed, this is what I get...

```
mark@mark-desktop:~$ sudo apt-get remove gtk-qt-engine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gtk-qt-engine is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libqt3-mt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by carterrocks on 2008-04-15
bump

---

### Post by carterrocks on 2008-04-15
Bump...

---

### Post by kellemes on 2008-04-15
> **carterrocks said:**
> I used the command but the terminal says it isn't installed, this is what I get...

```
mark@mark-desktop:~$ sudo apt-get remove gtk-qt-engine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gtk-qt-engine is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libqt3-mt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Well, you can do..
```
sudo apt-get autoremove
```
This will remove unwanted packages (1 to be exact) but it won't fix your problem.:(

I can only recommend googling a bit using the output of your message.

---

### Post by carterrocks on 2008-04-15
Got rid of Firefox 3 and installed Firefox 2

---

### Post by eXtreem on 2008-04-16
I solved the closing-problem by giving this command:

```
sudo mv /usr/lib/libflashsupport.so /usr/lib/libflashsupport.so.org
```

The problem existed at my installation too, but only when I was watching flash video's like youtube. Als after renaming flashsupport.so the video's are still working fine...

Grtzz eXtreem

---

### Post by marlun on 2008-04-17
I've got the same problem and I get the same output in the terminal.

---

