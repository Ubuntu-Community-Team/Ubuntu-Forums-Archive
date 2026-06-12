---
title: "Trusty 14.04.1 Gnome Flashback Alltray issue"
date: 2014-08-25
forum: General Help
---

### Post by cscj01 on 2014-08-25
I have a perculiar issue with Alltray under Trusty 14.04.1 x64.  When I use Alltray to dock an application, the icon for the application does not show in the panel.  However, if I check Systems Monitor, both Alltray and the application are running.

I believe in Precise, there was one more instance of Alltray than applications docked.  So if I had one application docked, I would see two instances of Alltray.  If I had two applications docked, I would see three instances of Alltay.

Now I only see one instance of Alltray with one application docked, my calendar.  However, the alerts for appointments still pop up.  The problem is, I must launch my calendar again to see it, whereas before, I could just click the icon in the panel.

All help will be appreciated.

---

### Post by cscj01 on 2014-08-28
I tried the following```
alltray -d /usr/lib/sunbird/sunbird
command without args: /usr/lib/sunbird/sunbird
basename: sunbird
command: /usr/lib/sunbird/sunbird
win->title_time: 0
win->notray: 0
HAVE MANAGER WINDOW
win->libsyp_window id: 71303171
execute program: /usr/lib/sunbird/sunbird
lib is here: /usr/lib
old preload: (null)
preload string: LD_PRELOAD=/usr/lib/liballtray.so.0.0.0
wait for window

(process:19198): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
```Perhaps someone can suggest what is going wrong?

Edit:  I forgot to add that the error message appeared when I clicked on the opened Sunbird window with the Alltray prompt showing.

---

