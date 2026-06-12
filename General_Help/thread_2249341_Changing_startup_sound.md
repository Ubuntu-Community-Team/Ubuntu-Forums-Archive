---
title: "Changing startup sound"
date: 2014-10-21
forum: General Help
---

### Post by pfeiffep on 2014-10-21
I've verified that is NOT currently the drum beat sound, but rather the desired sound.  Is there another location identifying the login sound?

Here's my current sound directory listing ... 
```
pfeiffep@Dell-Studio:/usr/share/sounds/ubuntu/stereo$ ls -l
total 364
-rw-r--r-- 1 root root   5016 Mar  2  2011 bell.ogg
-rw-r--r-- 1 root root   8997 Mar  2  2011 button-pressed.ogg
-rw-r--r-- 1 root root   4035 Mar  2  2011 button-toggle-off.ogg
-rw-r--r-- 1 root root   4035 Mar  2  2011 button-toggle-on.ogg
[COLOR=#ff0000]-rw-r--r-- 1 root root  29299 Mar  2  2011 desktop-login.ogg[/COLOR]
[COLOR=#ff0000]-rw-r--r-- 1 root root 104421 Oct 20 08:31 desktop-login.ogg.old[/COLOR]
-rw-r--r-- 1 root root  26925 Mar  2  2011 desktop-logout.ogg
-rw-r--r-- 1 root root  10660 Mar  2  2011 dialog-error.ogg
-rw-r--r-- 1 root root   5377 Mar  2  2011 dialog-information.ogg
-rw-r--r-- 1 root root   9851 Mar  2  2011 dialog-question.ogg
-rw-r--r-- 1 root root  12217 Mar  2  2011 dialog-warning.ogg
-rw-r--r-- 1 root root  22733 Mar  2  2011 message-new-instant.ogg
-rw-r--r-- 1 root root  10429 Mar  2  2011 message.ogg
-rw-r--r-- 1 root root  29299 Mar  2  2011 phone-incoming-call.ogg
-rw-r--r-- 1 root root   7996 Mar  2  2011 phone-outgoing-busy.ogg
-rw-r--r-- 1 root root   4792 Mar  2  2011 phone-outgoing-calling.ogg
-rw-r--r-- 1 root root  17274 Mar  2  2011 service-login.ogg
-rw-r--r-- 1 root root  14573 Mar  2  2011 service-logout.ogg
lrwxrwxrwx 1 root root     19 Oct 19 22:00 system-ready.ogg -> dialog-question.ogg
-rw-r--r-- 1 root root   6994 Mar  2  2011 window-slide.ogg

```

---

### Post by deadflowr on 2014-10-21
Look at /usr/share/gnome/autostart
You will see a file marked "GNOME Login Sound"
You can drag and drop into gedit, or other text editor to look at its contents.
Typically if it is enabled it'll say

X-GNOME-Autostart-enabled=true
changing that to false should disable it.
You would need to do that as root(sudo) though.

---

### Post by pfeiffep on 2014-10-21
> **deadflowr said:**
> Look at /usr/share/gnome/autostart
You will see a file marked "GNOME Login Sound"
You can drag and drop into gedit, or other text editor to look at its contents.
Typically if it is enabled it'll say

X-GNOME-Autostart-enabled=true
changing that to false should disable it.
You would need to do that as root(sudo) though.Thank you ... I found the directory path which contained libcanberra-login-sound.desktop so I copied my desired sound there naming it appropriately. I'm somewhat confused because I don't use autostart.

Changing libcanberra-login-sound.desktop did NOT change the sound.  Perhaps there's another file in play here ... 
```
lrwxrwxrwx 1 root root     19 Oct 19 22:00 system-ready.ogg -> dialog-question.ogg
```

What is the name of the sound file that plays when the login prompt presents?

---

### Post by pfeiffep on 2014-10-21
Changing the link destination changed the sound played when login prompt is presented.

So in my case I changed the target sound file in this link
lrwxrwxrwx 1 root root     19 Oct 19 22:00 system-ready.ogg -> dialog-question.ogg

---

