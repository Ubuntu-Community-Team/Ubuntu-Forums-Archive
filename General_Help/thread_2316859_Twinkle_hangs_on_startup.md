---
title: "Twinkle hangs on startup"
date: 2016-03-11
forum: General Help
---

### Post by VanillaMozilla on 2016-03-11
The system monitor shows twinkle is running, but the ikon does not appear in the system tray, and the GUI does not appear.  The System Monitor will not end the process; I have to kill it.  The problem appeared suddenly; the program has been working flawlessly for years.  The problem occurs from all user accounts, so it is not a profile problem.

When starting from terminal, I get the following dialog (user id info x'ed out), with no error messages:

~$ twinkle
Twinkle 1.4.2, February 25 2009
Copyright (C) 2005-2009  Michel de Boer

Users:
* xxxxx
    xxxxxxx <sip:xxxxxx@sip.diamondcard.us>

Local IP:       255.255.255.255


xxxxxxx: registering phone...

Twinkle> 
xxxxxx: registration succeeded (expires = 3600 seconds)

====================
Ubuntu 14.04, fully updated.  Any ideas?

---

### Post by v3.xx on 2016-03-11
Your trying to use a package (version) that is dated 2009?  I don't hold any hope for that.

What about this?

[http://twinkle.dolezel.info/](http://twinkle.dolezel.info/)

That will give you half a chance.

---

### Post by VanillaMozilla on 2016-03-11
Thanks.  That's just an old copyright splash, not the package date.  The date on the executable is actually Feb 1, 2014.  The SIP account was recharged from Twinkle on April 16, 2015, so the program was definitely working at that time.

I can only assume that a Ubuntu update broke the package.  This is a problem, because when I installed it, it was the only SIP program I could find that actually worked.  I still want SIP capability.  Any suggestions?

---

### Post by VanillaMozilla on 2016-03-12
Thanks.  I'm not going to try to compile this myself, especially since there is some leisurely activity to fix it.

There is a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/twinkle/+bug/1337997](https://bugs.launchpad.net/ubuntu/+source/twinkle/+bug/1337997) (twinkle no longer a GUI app???) and
[https://bugs.launchpad.net/ubuntu/+source/twinkle/+bug/1400112](https://bugs.launchpad.net/ubuntu/+source/twinkle/+bug/1400112) (Twinkle not working).

These are marked as duplicates of
[https://bugs.launchpad.net/ubuntu/+source/twinkle/+bug/1533561](https://bugs.launchpad.net/ubuntu/+source/twinkle/+bug/1533561) (wording on first run of twinkle-console could be improved).  It is marked as Low Importance, which is rather discouraging.

There are reports that Yate actually works.  Will install and try.

---

### Post by v3.xx on 2016-03-12
Sounds like a better choice.  Yate is already in Ubuntu software sources, no need for third party download.

---

### Post by VanillaMozilla on 2016-03-13
Unfortunately, Twinkle is also in Ubuntu sources, even though it doesn't work at all. :(

---

### Post by v3.xx on 2016-03-13
> **VanillaMozilla said:**
> Unfortunately, Twinkle is also in Ubuntu sources, even though it doesn't work at all. :(
Your right, I must of had a typo first time I checked.

```
~$ apt-cache policy twinkle
twinkle:
  Installed: (none)
  Candidate: 1:1.9.0+dfsg-3
  Version table:
     1:1.9.0+dfsg-3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
```

---

### Post by VanillaMozilla on 2016-11-26
There has been some progress.  Twinkle now works in 16.04, but with reduced functionality.  I have started a separate thread for that, here:  [https://ubuntuforums.org/showthread.php?t=2344569&p=13575270#post13575270](https://ubuntuforums.org/showthread.php?t=2344569&p=13575270#post13575270) .

---

### Post by VanillaMozilla on 2016-11-26
I previously reported that Twinkle (SIP phone) was completely nonfunctional.  [https://ubuntuforums.org/showthread.php?t=2316859&p=13575238#post13575238](https://ubuntuforums.org/showthread.php?t=2316859&p=13575238#post13575238)

It's working in Ubuntu 16.04, but with reduced functionality.

1. I can't use it to recharge my account or view any account information.

2. The system notification icon is gone.  If you close the window, Twinkle remains running, but there's no way to access the UI again.  You can't even close it unless you forcibly terminate it.  The latter was probably caused by [https://bugs.launchpad.net/ayatana-design/+bug/974480](https://bugs.launchpad.net/ayatana-design/+bug/974480) .  Is there a current workaround?

---

### Post by wildmanne39 on 2016-11-26
Please do not post duplicates, it dilutes community effort. Threads merged

---

### Post by mc4man on 2016-11-26
> **VanillaMozilla said:**
>  The latter was probably caused by [https://bugs.launchpad.net/ayatana-design/+bug/974480](https://bugs.launchpad.net/ayatana-design/+bug/974480) .  Is there a current workaround?
Patch & rebuild unity to enable the systray (i.e., re-whitelist), basic patch, line numbers may vary slightly depending on unity version

```
--- a/panel/PanelTray.cpp
+++ b/panel/PanelTray.cpp
@@ -134,7 +134,7 @@
   glib::String res_name;
   na_tray_child_get_wm_class(icon, &res_name, &res_class);
 
-  bool accept = FilterTray(title.Str(), res_name.Str(), res_class.Str());
+  bool accept = true;
 
   if (accept)
   {
--- a/tests/CMakeLists.txt
+++ b/tests/CMakeLists.txt
@@ -250,7 +250,6 @@
                  test_panel_menu_view.cpp
                  test_panel_service.cpp
                  test_panel_style.cpp
-                 test_panel_tray.cpp
                  test_panel_view.cpp
                  test_places_group.cpp
                  test_preview_player.cpp

```

---

### Post by VanillaMozilla on 2016-12-13
Thanks mc4man.  I don't think I will be rebuilding Unity any time soon, but that may be helpful for someone else.

---

