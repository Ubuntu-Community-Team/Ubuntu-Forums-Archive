---
title: "Ubuntu 13.04 crashes at startup - I can get Terminal working"
date: 2013-05-10
forum: General Help
---

### Post by abcuser on 2013-05-10
Hi,
I have been running Ubuntu 13.04 for some days now and everything was working fine. Today I have turned on computer and after a while I got an error message: "System program program detected. Do you want to report the problem now?" and clicking on Cancel button and there is only background image and mouse pointer. So there is no launcher and no top panel (where clock is and shut-down etc).

I can fire a Terminal by CTRL+ALT+T and I can run any GUI program from terminal like e.g.:
nautilus
firefox
libreoffice --writer
software-center

**Not working keyboard shortcuts:**
Super+1 to launch file manager. Super+any_number also does not launch any other program from Launcher.
ALT+TAB to switch between programs.

**Working keyboard shortcuts:**
Super+D to minimize windows
CTRL+Super+left to expand window to only half of the left screen
CTRL+Super+Up to get windows in maximize state
CTRL+Super+Down to get windows in state before maximize.

How to solve this problem? How to get Unity back?

Regards

---

### Post by 2F4U on 2013-05-10
Are there any details available about that problem, e.g. which program crashed? If I remember correctly, the crash box should provide the option to get more detail, maybe upon deciding to report the problem.

---

### Post by abcuser on 2013-05-13
@2F4U, I clicked on Report problem button when crash appeared and bellow is the few lines of text (I had to type them down):
==========
Crash report: Sorry, the application add-apt-repository has stopped unexpectedly.
Executable Path: /usr/bin/add-apt-repository
Package: software-properties-common 0.92.17
Problem Type: Crash
Title: add-apt-repository crashed with ImportError in get_ppa_info_from_lp(): NoModule named 'pycurl'
==========
There are many other lines, I need to manually type them down. I see no copy/paste feature in this crash report window, what a pity. When I scroll down on this crash window then whole Ubuntu crashes with X-server failure, so I can't type more text.

Any idea how to fix the problem?
Thanks

---

