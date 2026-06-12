---
title: "Disable window manager"
date: 2017-07-12
forum: General Help
---

### Post by bask185 on 2017-07-12
I have a Qt application on a ubuntu 16.04 device with the default desktop environment. I want this Qt app to run entirely fullscreen. Qt offers a solution for that but! If I open a sub-window like the virtual keyboard it appears in a window and that lets the desktop environment 'shine' through my application and that is kinda annoying. On the Raspberry Pi with Raspbian I never had this problem because there was no window manager for the Qt application.

Idk how I can solve the problem. Can I disable this window manager? The device's sole purpose is to run the application. Or do I need to download a different desktop environment?

I also posted this here: [https://forum.qt.io/topic/81209/fullscreen-application-in-ubuntu](https://forum.qt.io/topic/81209/fullscreen-application-in-ubuntu)

---

### Post by deadflowr on 2017-07-12
Try setting an X session for the app.
Do something like this:
[https://askubuntu.com/questions/310671/start-ubuntu-without-a-desktop-environment-but-start-an-x-application]("https://askubuntu.com/questions/310671/start-ubuntu-without-a-desktop-environment-but-start-an-x-application")
or try setting up a non-display manager setup, like something in here:
[https://superuser.com/questions/904142/launching-programs-with-gui-without-display-manager]("https://superuser.com/questions/904142/launching-programs-with-gui-without-display-manager")

But basically, yes you can set it up to run without a window manager or desktop environment, or even a display manager.

---

### Post by bask185 on 2017-07-12
The answer of the first link did the trick. Somebody on the Qt forum was already scaring me little bit with setting up a kiosk mode ;)

It is nice because it also auto-boots to the app without having to make changes to rc.local and such.

EDIT:
I am having 2 huge problems with this method:

The first problem is that I cannot set up a serial connection. I know that this is because the serial ports (atleast the USb port) have no permissions. As I launch the app via a shellscript I added a line of code before the app starts. I added ```
sudo chmod 777 /dev/tty*
```. If I boot to the normal desktop and run this shellscript I need to enter my password and it works. Than I can log out and log into the GUI desktop and then it can set up a connection. But if booting to the GUI desktop is the first thing of the day, it won't set up a serial connection. So that is a problem. I just have to fill in the damned password before I can connect.

The second problem is that I have no longer an output on the CLI. If I run into a bug I need to be able to see the last  transfer on the CLI to find the bug. I also need to be able to close the app and restart it via SSH so I can have the debug texts on my work PC. But this also cannot be done.

What would solve atleast problem #2 is that I would start the CLI rather than my own shellscript. Than I can add my shellscript to .bashrc so the app gets started via the CLI. But I doubt if this will fix problem #1.

2nd EDIT:
I added my user account to the group dialout, this solves the serial connection problem. The other problem of not being able to use the CLI will be solved in the form of a log file. Than I can open it on the device and I get to SCP it to my work PC.

This day is a win!

---

