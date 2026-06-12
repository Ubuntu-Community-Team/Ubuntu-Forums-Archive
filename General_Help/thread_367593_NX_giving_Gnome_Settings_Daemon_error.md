---
title: "NX giving Gnome Settings Daemon error"
date: 2007-02-22
forum: General Help
---

### Post by Roman27 on 2007-02-22
I must say that NX had been working great for me.  I had been using FreeNX on Ubuntu since Hoary.  I installed the latest from nomachine using instructions from this board about a week ago.  All was good.  It was super fast even at 1280x1024.  I was loving it.

But this morning, I go to logon from my remote machine and it gives me a black screen for about 5 minutes before displaying this:

[[IMG]http://img519.imageshack.us/img519/5650/screenshotnxxz6.th.png[/IMG]](http://img519.imageshack.us/my.php?image=screenshotnxxz6.png)

I close that message and another 5 minutes or so goes by before the icons on the desktop appear, along with the usually bug crash catcher (which has always happened since I've started used NX with Edgy).  But the task bars never appear.  I wind up hitting ALT-F4 and terminating the session.

I've tried rebooting several times today and it hasn't helped.  In the past week, I made a change to shut off IPv6 and I've installed the ntp stuff to keep my machine up to day.  So, I went through and uninstalled all that using apt-get, which I never use so that was fun to learn how to do all that through an SSH session remotely.  :)

Here are the versions of the NoMachine applications I installed.

nxclient 2.1.0-11
nxnode 2.1.0-15
nxserver 2.1.0-18

Does anyone have a clue why this would happen all of a sudden?  The only thing I can think of is that this is the first reboot after the installation of the NX stuff.  Ubuntu is just so darn solid there's not really a need to reboot, but I did reboot last night after following the instructions to disable IPv6.

---

### Post by roobarb! on 2007-05-11
I've had a very similar problem to this, but I've also not managed to find a permanent solution that keeps all the features of NX server working. Most of the suggestions centre around removing .gconf and .gnome folders from my home area. Don't bother - it makes no difference. This is the error I was getting:

> There was an error starting the GNOME Settings Daemon

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

What does make an instant difference is turning off the multimedia support in the NX Client (this is the Windows version of the client, v2.1.0-17, anyway). Hit 'Configure', then go to 'Services', then just untick 'enable multimedia support' and save.

Logging on becomes nice and swift again, although you obviously lose the sound, which is disappointing. If you can stand the wait and the error message, then just leave multimedia services on - it works fine once you're in. You just need patience... I've Googled, but not managed to find a proper fix for this - although if anyone out there has I would be very happy to hear it!

Hope that helps someone out there not get as impatient as I have been getting... :)

---

### Post by the.dark.lord on 2007-05-11
I have exactly the same darn problem!!!!!!!!!!!!!!!!!!! 

roobarb, can you please explain your solution in a more noobish language ;) ?

---

