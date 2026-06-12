---
title: "Chrome and Chormium cause segfault"
date: 2012-12-20
forum: General Help
---

### Post by dannyboy79 on 2012-12-20
I was running chromium happily since I installed 12.04 64bit xubuntu about a week ago and yesterday I purchased the humble bundle 7. 3 of the games were allowed to be installed from the Ubuntu Software Center. I installed all those and then remembered I had tried out steam linux beta and purchased Serious Sam 3 BFE when I was trying out Linux Mint 14 w/ Mate (this was prior to switching to Xubuntu).

I proceeded to install Steam again and when it came time to enter an emailed code from steam to verify the computer, chromium crashed and actually went all the way back to the lightdm greeter (or whatever it's called where you enter username and password to login) So basically a full X crash. I relogged in and tried to open chromium again and X crashed again. What was in the kern.log was a segfault for gnome-keyring-deamon. Well, I uninstalled chromium and stuck with firefox but realized I needed either chrome or chromium for my syncd passwords and bookmarks from my gmail address so I installed google chrome and that crashes even worse, tty7 goes to a black screen with text on it and even going to tty1 and logging in, then killing lightdm and trying to restart it does the same thing, no X server (GUI) will start. Have to do a full restart to get back into a GUI

I can't find anything in kern.log, syslog, Xorg.0.log, or .xsession-errors that points to what is causing the X crash but I can't use either chrome or chromium anymore and I really need it. I even tried uninstalling Steam to no avail, chromium and chrome both still crash X completely. I notice when removing chromium that it removes a ton of :i386 stuff, I know I downloaded the 64 bit version of chrome. Not sure about chromium-browser as that was in the repos.

Any thoughts? I'll post any files or pictures, hell, even a video to my youtube channel showing the crash. Thanks

---

### Post by dannyboy79 on 2012-12-21
i ended up renaming the ~/.config/chromium folder to chromium_OLD and reinsatlled chromium. I remember something I did 1 time when I opened steam, it prompted me to install the latest 310 nvidia driver and I clicked yes which brought up jocky but I hit cancel as I already had the latest 310.19 version. I am wondering if some how the nvidia driver installed files got messed up BUT I eneded up changing from the 310.19 nvidia binary to the updates-latest which is 304.64 and now everything is working again. Steam works, Chromium works and all is well again.

---

