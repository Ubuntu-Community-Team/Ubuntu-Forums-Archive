---
title: "Opera taking minutes to start"
date: 2018-08-06
forum: General Help
---

### Post by carlo-sanguineti on 2018-08-06
Hello

I use Opera without any Java or other scripts just to browse in sites I'not sure about security or annoying popups.
My Opera is:
Version:	54.0.2952.64 - Opera is up to date
Update stream:	Stable
System:	Ubuntu 18.04.1 LTS (x86_64; ubuntu:GNOME)


Everything went OK until three weeks ago. After this Opera takes at least two minutes to start, and off course I don't know what to do. I am a "final user" on Ubuntu, and my skill is limited. I know computers since a lot of time (on August 13th I will be 62) but I never worked on Unix, Linux, etc. Just old DEC (Digital), DOS and Windows.
What can I say more? I have two more problems, and I don't know if they are connected with my Opera problem:
1. I had the bad Idea of installing tvmosaic on my PC: It doesn't work and get an amazing lot of RAM memory. The only solution I found by myself until now is to kill it by Terminal on every login.
2. I have quite often a problem on starting some application. For example, if I click on the Easytag or Terminal or JDownloader icons nothing happens. If I go on Activities and try to start them from there I receive the message "Failed to Fork - Cannot allocate memory". But if I go "Files" and I open a directory in Terminal it works. So, from Terminal, I can open, for example, Easytag and it works, despite on terminal I receive the message "(easytag:15501): Gtk-CRITICAL **: 14:07:41.073: gtk_widget_grab_focus: assertion 'GTK_IS_WIDGET (widget)' failed"

As I wrote before I really don't know if the problems are connected or not. I would be really glad if somebody could help me.
Thank you in advance,

Carlos

---

### Post by Claus7 on 2018-08-11
Hello,

since you suspect that is a memory issue (and since you get messages related to memory) issue the command:
free -m

to check how much memory is in use. If is too high, then you can use the command:
top -n 1

to check at that time, which is the memory consumption per application/command.

You can try that directly on boot, prior of killing tvmosaic, and after killing it, so as to check if this is the cause of your problem and how much your action affects the memory consumption.

Some processes have more that one command running, so killing one, might not entirely eliminate it from running, so you should verify how is killed.

Regards!

---

