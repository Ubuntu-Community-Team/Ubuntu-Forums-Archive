---
title: "X screen saver"
date: 2016-02-26
forum: General Help
---

### Post by jerry50 on 2016-02-26
Whenever I try to use the screen saver that comes with Trusty Tar I get this message:  "The XScreenSaver daemon doesn't seem to be running on display ":0".  Launch it now?"  I click OK and it works, but how can I make this work without getting that message?

---

### Post by jerry50 on 2016-02-26
OK...looked around a bit and found something.  I should add the following to the startup application, right?  
xscreensaver -no-splash

---

### Post by jerry50 on 2016-02-26
Nope.  Just restarted computer and still get the same message:  "The XScreenSaver daemon doesn't seem to be running on display ":0".  Launch it now?"

---

### Post by Dennis N on 2016-02-26
You are correct. Also, be sure any other screensaver, such as gnome-screensaver, is disabled in startup applications.

---

### Post by jerry50 on 2016-02-26
I don't have the gnome screen saver in the apps or anywhere else that I can find.  Still doesn't work.  And, I'm suppose to put that command in the start up apps, right?  Not the terminal?  Because it is in the start up but it still doesn't start on its own.

---

### Post by furtom on 2016-02-26
Which flavor are you running? Ubuntu, Lubuntu, Xubuntu, etc.

---

### Post by Dennis N on 2016-02-26
> **jerry50 said:**
> I don't have the gnome screen saver in the apps or anywhere else that I can find.  Still doesn't work.  And, I'm suppose to put that command in the start up apps, right?  Not the terminal?  Because it is in the start up but it still doesn't start on its own.

gnome-screensaver	3.6.1-0ubuntu13 

is installed by default in Trusty. It is probably identified just as 'screensaver' in the startup applications dialog. Be sure the box in front of screensaver is unchecked, and that the box for xscreensaver is checked. See the attached screenshot of dialog window.

---

### Post by jerry50 on 2016-02-26
I'm using ubuntu 14.04 trusty tar.    The screen saver is XScreenSaver 5.15, 28-Sep-2011...that's what it says at the top.  And in the startup applications I only have 4 things:  GPG Password Agent, Indicator Application,  SSH Key Agent, and now xscreensaver -no-splash.  That's it.  No Gnome Screen Saver.  No where.

---

### Post by Dennis N on 2016-02-26
> **jerry50 said:**
> ubuntu 14.04 trusty tar.    The screen saver is XScreenSaver 5.15, 28-Sep-2011...that's what it says at the top

That's the version used in Ubuntu 12.04. Could you be running that (codenamed Precise)? In any case, it does not matter which version of Ubuntu you are using, the procedure is the same. Recheck the command you entered in the command box when adding the new startup entry for spelling, hypens, and be sure no capital letters are used: 

```
**xscreensaver -no-splash**
``` Restart the computer.

---

### Post by Dennis N on 2016-02-26
I checked and Ubuntu 14.04 uses the same version 5.15 of xscreensaver, so all is o.k. as to the version.

---

### Post by Dennis N on 2016-02-26
> **jerry50 said:**
>  And in the startup applications I only have 4 things:  GPG Password Agent, Indicator Application,  SSH Key Agent, and now xscreensaver -no-splash.  That's it.  No Gnome Screen Saver.  No where.

OK, on rereading this, you mention here that just 4 things show up so I think I know the problem. The others are hidden by default by Ubuntu's creators. You need another command to make them visible. Here is the old post that contains the command to show all the startup applications:

[http://ubuntuforums.org/showthread.php?t=2203463&p=12918998#post12918998](http://ubuntuforums.org/showthread.php?t=2203463&p=12918998#post12918998)

That command will allow you to see and disable gnome screensaver. That said, I think xscreensaver should be starting anyway if it has a proper entry and it's checkbox is marked as discussed in post #7. We disable gnome screensaver so the two don't fight about which controls the screen saving.

---

### Post by jerry50 on 2016-02-26
Glad to hear I'm not running a weird version of Ubuntu.  And...just re-booted AND still getting that same message.  Oh well.... on a scale of 1 to 5 this is about as important as -2, so.... Thanks for trying.  We may never know why it doesn't want to work.  And by April, when the new LTS version comes out, it may be a moot point anyway.

---

### Post by Dennis N on 2016-02-26
One other thing you might check is if there is a .desktop file written for xscreensaver in ~/.config/autostart
It should have been created automatically when you entered information in the Startup Applications dialog.

Command to see it:
dmn@Roxanne:~$ cat .config/autostart/xscreensaver.desktop
What the file looks like on my computer:
```
[Desktop Entry]
Type=Application
Exec=xscreensaver -no-splash
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=Xscreensaver
Name=Xscreensaver
Comment[en_US]=xscreensaver program
Comment=xscreensaver program
```

---

