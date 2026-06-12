---
title: "Help me connect to Oracle 11i server (Java PATH variable)"
date: 2006-11-22
forum: General Help
---

### Post by sarc on 2006-11-22
I am trying to login into Oracle 11i server, it needs Oracle's Java to run fonts, I have installed it as per Oracle discussion groups but don't know how to set the PATH variable.  Works in windows, not in Ubuntu.  Would someone be able to help me with this?  Using Firefox.  Thanks

The instructions from Oracle are:

In order to access this application, you must install the J2SE Plugin version 1.4.2_04 on your client and NPX_PLUGIN_PATH environment variable is set before starting Netscape. To install this plugin, click here to download the oajinit.exe executable. Once the download is complete, double-click the oajinit.exe file to install the plugin. You will be prompted to restart your browser when the installation is complete.

---

### Post by mark2741 on 2006-11-22
I'm not really familiar with oracle but perhaps from the instructions you quoted all you need to do is to set your PATH variable to include the directory where you placed the J2SE plugin?

Type this (in terminal) to find out what your path is currently set to:

echo $PATH

To set your PATH type: export PATH=whatever

where 'whatever' would be the file path to the plugin

Again - I'm just guessing. But it may be worth a shot.

---

### Post by sarc on 2006-11-23
Thanks for suggestion, the reusult seems really strange to me - something wrong with my java?

echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

$ java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

---

### Post by mark2741 on 2006-11-23
Try adding the path to the orajint plugin to the beginning of the PATH variable. I remember a couple of years ago a program at work had an issue with Oracle where something needed to be added to the beginning of the environment variable or else Oracle picked up the wrong one.

---

