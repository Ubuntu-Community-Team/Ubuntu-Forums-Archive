---
title: "Bluetooth Mouse Connection Problem"
date: 2013-12-16
forum: General Help
---

### Post by histamineblkr on 2013-12-16
I have searched the forums and checked on google but I haven't come across my specific problem so I will see if any of you fine people here can get me pointed in the right direction to find my bug. 

I have no problem connecting my bluetooth mouse and it working. The issue arises later during hibernation/sleep/screensaver.

**Misc Info:**

Running ubuntu: **12.04.3 LTS the 64 bit version**
Kernel version: **#49~precise1-Ubuntu**
Release: **3.8.0-34-generic**
Bluetooth manager: **Default in ubuntu** ( I already tried installing blueman to see if that would fix my issue, but the bug persisted )
Computer: **acer Aspire S7 with the included acer bluetooth mouse**

[B]Problem/Bug:

[/B]The acer bluetooth mouse looses its connection after I resume from a sleep/suspend. I can duplicate the error every time by connecting my mouse and then putting the computer to sleep by closing the lid. It will also happen if I let the computer timeout and go to sleep. Upon returning from sleep and logging back in my mouse has no connection. I have tried to reconnect it by using the bluetooth button on the mouse, reconnecting it in the bluetooth settings, deleting the pairing and pairing it again, and  starting and stopping the bluetooth connection through the terminal (service command). None of that works.

The connection between the mouse and manager only stops with the suspension.

[B]Fix:

[/B]The only fix I have come up with is to log out and back in, where upon the mouse connects itself automatically. I have had some luck with disconnecting the mouses' bluetooth connection before suspending but that seems to be intermittent. 

This is not really a fix since it kills everything you had loaded or were working on.

[B]Theories:

[/B]I do use XScreenSaver 5.15 with Electric Sheep and uninstalled the GnomeScreenSaver (Possible bug introduction with that?), but am thinking not since I remember this problem while running the LiveOS during installation. 

Since the problem happens during a suspension I am guessing something with the connection is hanging and is only finally terminated during the log out. I have tried to terminate everything I can think of manually to do with the bluetooth connection but am missing something since it's solved during a log out.

[B]Help:

[/B]I am pretty capable when it comes to Linux, I am not a newbie. If given some direction of where and how to look for the problem I can spend the time looking for the bug and trying to solve it, just point me in the direction. I am stumped on how and where the connection is hanging (if that's actually what is happening). If you read this and already know what the problem is, great! That makes all of our lives easier =D

[B]Missing:

[/B]If I left out anything or you need more info or whatever just let me know and I'll provide it as soon as I can. 

Thank you in advance for all your help.

---

### Post by histamineblkr on 2013-12-17
[B]Update:
[/B]
I have figured out that if I turn my mouse off, then disconnect it from the bluetooth menu, and then put the computer to sleep I can resume and reconnect the mouse and it works. While testing different sequences of events out, I noticed that my mouse would connect back with bluetooth most of the time (the blinking light on the mouse would do its quick connect blink) but the mouse cursor would remain unresponsive. The only way I could get it to work was by doing exactly the method describe above.

---

