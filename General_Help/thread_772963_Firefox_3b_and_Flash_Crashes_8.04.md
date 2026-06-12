---
title: "Firefox 3b and Flash Crashes 8.04"
date: 2008-04-28
forum: General Help
---

### Post by czechman86 on 2008-04-28
I have been having several crashes in Firefox, while I am watching a video on youtube. I decided to run FF via the terminal and here is the output I received during one of those crashes:

```
czechman86@uBox:~$ firefox
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
GCJ PLUGIN: thread 0x805e128: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805e128: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805e128: NP_GetValue
GCJ PLUGIN: thread 0x805e128: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805e128: NP_GetValue return
GCJ PLUGIN: thread 0x805e128: NP_GetValue
GCJ PLUGIN: thread 0x805e128: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805e128: NP_GetValue return

(firefox:8294): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8294): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8294): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8294): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8294): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8294): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

```

Anyone else having this problem? Anyone have any idea for fixes?

I have run memtest 3x and the memory is fine, this appears to be an allocation issue. Could this be a result of the beta? 

I have also installed the pulseaudio fix for FF and flash.

Thanks!

---

### Post by FredB on 2008-04-28
Just trash adobe flash. Try swfdec, it works with youtube without problem and don't make firefox crashing.

---

### Post by SamSlater on 2008-04-28
I'm having similar issues. Not just youtube but listening to radio in last.fm too. not just Firefox either because Epiphany crashes also so I'm guessing it's the flash plugin rather than Firefox.

Wish someone could help with this issue because it's real annoying. :(

---

### Post by FredB on 2008-04-29
Just try to use swfdec plugin instead of adobe one. I don't know if last.fm will work, at least youtube will.

---

### Post by czescik on 2008-05-15
the solution for this problem is here:

> [http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html](http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html)

---

### Post by yaknowwat on 2008-05-15
Yes this is an issue with libflashsupport and Flash I tried NSPluginWrapper for a while it worked nicely but as it turns out NSPlugin Wrapper kills alot of functionality of Flash so i had to just give up pulseaudio

Everytime the computer is started up i kill pulseaudio and i no longer have libflashsupport installed and things work normal again other then having to kill pulseaudio at startup :P

---

### Post by mike555 on 2008-05-15
I also had trouble with flash , but since uninstalling it and installing Flash 10 beta , no more troubles (so far) .........

---

