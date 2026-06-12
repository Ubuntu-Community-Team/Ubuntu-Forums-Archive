---
title: "Stuff in top bar gone"
date: 2013-11-12
forum: General Help
---

### Post by Glenneey on 2013-11-12
Hello guys!
I'm new to Ubuntu, so I apologise up front for me being a bother...
Anyway, my problem:
I recently did some editing, using compiz (or I think that's how it's called).
Now there's nothing in the top bar any more (time, sound, internet, etc)  it just tells me what program I'm using.
I also no longer have sound, nor does my microphone work anymore (tried skyping, failed horribly).
Here's a screenshot of the problem: [IMG]http://i296.photobucket.com/albums/mm171/glenneey/Screenshotfrom2013-11-12210507_zpsaa975433.png[/IMG]


I hope you can help me,
Thanks.

---

### Post by philinux on 2013-11-12
Reset compiz and unity.

[http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/](http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/)

---

### Post by Glenneey on 2013-11-12
Thanks for the quick reply, unfortunately after following that guide all that's happened is that my launcher icons have reset to the original settings.
The top bar is still completely empty except from the text on the left giving info about the current page.
I hope you can help me fix this,
Thanks.

---

### Post by jamesisin on 2013-11-12
Can you give us the steps by which you created this problem (as much detail as possible) so we might help you in reversing it?

---

### Post by Glenneey on 2013-11-12
I will try and recall all I did before this occurred.
I installed compiz, and opened it by typing in ccsm in the dash.
Then, after accidentally pressing 3D windows, my desktop went crazy, and I decided to reboot my computer.
After the reboot, my launcher was gone, because the unity plugin wasn't enabled, I enabled it and my launcher returned, but the top bar stays empty and the sound/mic was also not working anymore.
I also checked out the 3D windows thing, but that was already disabled after the reboot.
Hope I gave you some info,
Thanks.

---

### Post by philinux on 2013-11-12
sudo apt-get install --reinstall indicator-session

Try that.

---

### Post by Glenneey on 2013-11-12
After trying that, nothing happened.
To be sure I rebooter after that, but unfortunately, still nothing.
I hope I haven't completely ruined my system...
Thanks

---

### Post by jamesisin on 2013-11-12
Does ccsm store it's changes in a config file which we might rename and thus revert configurations?

---

### Post by Glenneey on 2013-11-12
I removed the config, i looked up where it was located.
Did not work either.
This is... stressing me out to say the least, I'm not used to this OS and have no idea what I did, and no idea how to fix it either..
I hope you guys can help me
Thanks

---

### Post by jamesisin on 2013-11-12
Create a different user account and log in as that user.  See if it persists with a new user.  If it does not, we know the problem is somewhere in your ~ bucket.

---

### Post by Glenneey on 2013-11-12
I'm trying to, but this + button is greyed out, and it told me before somewhere that I needed to unlock to enable. There's also a greyed out (unclickable) button above my account info say (unlock).
Any ideas how to fix this?
Thanks

---

### Post by jamesisin on 2013-11-12
Use the padlock in the upper-right corner.

---

### Post by Glenneey on 2013-11-12
I tried to, but the + button is greyed out, and somewhere else it tells me I need to unlock my account.
There's a grey unclickable 'unlock' button too, but as I said, I can't click it..
help?
Thanks

---

### Post by Glenneey on 2013-11-12
Sorry for the doublepost, something went wrong..
ill try

---

### Post by jamesisin on 2013-11-12
Is your account listed as Administrator?  If your account type is Standard, you'll need to log in as an administrator.

---

### Post by Glenneey on 2013-11-12
What padlock are you talking about?
There's one, the one I mentioned in my earlier post, it has 'unlock' next to it but I can't click it.
Thanks

---

### Post by Glenneey on 2013-11-12
Yes. I am listed as Administator.

---

### Post by jamesisin on 2013-11-12
Are you able to issue commands using *sudo* at present?

```
sudo ls -al /
```

---

### Post by jamesisin on 2013-11-12
If you can run sudo commands, then you can launch User Accounts as root.

```
gksudo gnome-control-center
```

Be very careful what you do with System Settings open in this manner as you can (without any warning) really muck things instantly.

Just create a test user (Admin or Standard shouldn't matter) and set a password.  Then close it.

Log out as yourself and log in as this new user.  See if the top bar looks as expected or not.

See you soon.

---

### Post by philinux on 2013-11-13
> **jamesisin said:**
> If you can run sudo commands, then you can launch User Accounts as root.

```
gksudo gnome-control-center
```

Be very careful what you do with System Settings open in this manner as you can (without any warning) really muck things instantly.

 That's not a good idea. 


> Just create a test user (Admin or Standard shouldn't matter) and set a password.  Then close it.

Log out as yourself and log in as this new user.  See if the top bar looks as expected or not.

See you soon. Creating another user is a good idea at this point.

---

### Post by Glenneey on 2013-11-13
Thanks a bunch for the help so far, but unfortunately when I try using a different user account the problem still remains.

---

### Post by philinux on 2013-11-13
To be honest you could waste hours on this. I would reluctantly reinstall.  Back up etc first.
It will be quiquicker.

---

### Post by Glenneey on 2013-11-13
I found that when I try to do 'setsid unity' it does the following:
My screen flashes a few times, and I get this output:
glenn@GlennsRig:~$ setsid unity
glenn@GlennsRig:~$ compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service: no process found
glenn@GlennsRig:~$ compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: commands
compiz (core) - Info: Starting plugin: commands
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
WARN  2013-11-13 15:48:54 unity.glib.dbus.server GLibDBusServer.cpp:586 Can't register object 'com.canonical.Autopilot.Introspection' yet as we don't have a connection, waiting for it...
WARN  2013-11-13 15:48:54 unity.glib.dbus.server GLibDBusServer.cpp:586 Can't register object 'com.canonical.Unity.Debug.Logging' yet as we don't have a connection, waiting for it...
WARN  2013-11-13 15:48:54 xim.controller XIMController.cpp:90 IBus natively supported.
WARN  2013-11-13 15:48:54 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2013-11-13 15:48:54 unity.libindicator <unknown>:0 No name available for nick 'X-New'
WARN  2013-11-13 15:48:54 unity.glib.dbus.server GLibDBusServer.cpp:586 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
WARN  2013-11-13 15:48:54 unity.glib.dbus.server GLibDBusServer.cpp:586 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
WARN  2013-11-13 15:48:54 unity.glib.dbus.server GLibDBusServer.cpp:586 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct


Can this mean anything?

---

### Post by philinux on 2013-11-13
Try this. 

gsettings reset org.compiz.core:/org/compiz/profiles/unity/plugins/core/ active-plugins

---

### Post by Glenneey on 2013-11-13
Still the same.
Do you think we'll be able to fix this?
I'd rather not install Ubuntu again, cause I think I'd lose all the stuff that I did, which cost me a lot of time to set up.
Thanks

---

### Post by jamesisin on 2013-11-13
If it is any consolation, I have written a short guide for myself when I build Ubuntu machines.

[http://jamesisin.com/a_high-tech_blech/index.php/buildubu/](http://jamesisin.com/a_high-tech_blech/index.php/buildubu/)

I was really hoping a new user would not see the issue since that would mean (at worst) we could merely delete your current home directory and allow the system to create a new one for your user account.

As it stands, whatever you did is system-wide.  It could be very difficult indeed to tease out where the problem lies.

C'est la vie.

---

### Post by Glenneey on 2013-11-13
After reinstalling ubuntu, the problem has been fixed.
Thanks a lot for your help, I greatly appreciate it.

---

### Post by philinux on 2013-11-13
Be very careful with compiz config settings manager. Here be dragons. 

Glad you're sorted. I hate having to recommend reinstall but on the rare occasions it's the only way. Been here too with unity in 12.10. My meddling too. I even deleted most of my home folder and it was still borked. But there you go.

---

