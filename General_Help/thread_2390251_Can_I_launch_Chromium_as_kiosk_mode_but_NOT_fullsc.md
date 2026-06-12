---
title: "Can I launch Chromium as kiosk mode but NOT fullscreen?"
date: 2018-04-27
forum: General Help
---

### Post by webmiester on 2018-04-27
Hi guys,

I am making a web-based application where I want to hide the address of my main server from users, but at the same time my users still need to connect to other websites using the browser.  Ill be using Chromium as the browser for my main application (Firefox has sound issues on my machines).

Right now what I am doing is to launch chromium in kiosk mode.  However, this covers the entire screen and there is no way to open other programs, unless the users close chromium (not minimize).

What I would like to do is to have the ability to still hide my address bar (so that users wont know the address of the application server), but they will still have the capacity to minimize the Chromium kioisk window and open another instance of chromium with the address bar present.  So in short, I can have 2 windows of Chromium, with 1 window having its address bar hidden, and the other one having its address bar present.  Or an alternative is have a chromium window open without address bar and have another browser (such as firefox) open with its address bar present.

Is this possible?  Thank you.

I am using Ubuntu 16.04 running on a Raspberry Pi.  I know its not x86 based, but so far almost all the commands and configurations for the x86 Ubuntu works on this one too.  So if what you know works on an x86, it is worth a try on this one.

Thank you in advance

---

### Post by TheFu on 2018-04-27
Interesting problem.

Alt-F2 doesn't work?  What about F11?   Both blocked/remapped?

I googled for kiosk solutions and found 1, but don't know anything more about it.  Didn't see any pricing, but it was a corporate offering. They listed specific keys their solution blocked.

Then I played with kiosk mode and broke out of it. There are a bunch of dangerous keys that need to be captured. The underlying shell needs to be locked down too, bigtime.  And I'd make the file system read-only to prevent some other attacks.

For network blocking/whitelisting, disable DNS and use the /etc/hosts.  If you have more than a few systems, forcing a proxy server for all network access would provide  more centralized control, but that can be handled with ansible pretty easily too.

According to the chromium-browser manpage, there is a startup option --app= which removes all chrome from the browser window, but in my testing it doesn't go full-screen and there isn't an option to make it full-screen.  Previously, I've used xdotool to force F11 into the window, but in app-mode, that didn't work in my trivial testing. Something about app-mode seems to break it.

---

### Post by zctgbhu on 2018-07-05
--window-size=x,y --window-position=x,y --kiosk

---

