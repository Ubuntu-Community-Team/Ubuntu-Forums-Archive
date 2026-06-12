---
title: "TTY cursor blinks while on desktop"
date: 2013-02-26
forum: General Help
---

### Post by Roflcopterofl on 2013-02-26
Hello,
After installing my graphics card drivers I have noticed that the TTYs (the terminal you get by pressing ctrl alt f1) cursor appears while on my desktop. My computer boots to the desktop correctly, but sometimes I see a small black box (about the size of a on screen character) appear on the screen. If I attempt to go to the TTY while this issue is occuring nothing happens until after 5 minutes have past, at which point TTY opens and fills half the screen. After I close out of it at that point the cursor jumps to the center of the screen. I have noticed this issue only occurs after seeing the TTY screen flash while booting (it boots to the desktop then the issue occurs). Loging in and out fixes the issue.

Any idea how to fix this issue?
Thanks :D

---

### Post by matt_symes on 2013-02-26
Hi

Never ever heard of that one before. I would suggest posting these two logs...

```
/var/log/kern.log
/var/log/syslog
```...right after it happens again.  

As soon as you see it make a copy of those logs and post them here.

Any chance of some pics when it happens again  ?

They may be able to shed some light on and and point to other areas to get information on.

What i would do is raise a bug on launch pad as this one really does sound like a bug. Maybe some race condition or something.

After it happens at the terminal type

```
ubuntu-bug <package_name>
```I've no idea what <package_name> (maybe lightdm) should be though in this case. _suggestions from other are welcome as to the package._

Have a read of this

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

If it does turn out to be a bug you'll be doing Ubuntu a favour.

If you raise a bug don't do it the time you make any copy of logs to put up here. They need no tampering to bug hunt.

Kind regards

---

### Post by Habitual on 2013-02-26
> **Roflcopterofl said:**
> 
Any idea how to fix this issue?
Thanks :D

dunno about "fix", but try this:
Create a new user on the system, logout, and login as the new user and see if the problem persists. If it does not, then it's an issue with _your_* ~/.*config and/or ~/.gconf.

to start fresh with ~/.config and ~/.gconf do this:
Logoff and press Ctrl+Alt+F1 and login to the console _as yourself_
```
mv .config .config.org
mv .gconf .gconf.org
exit
```
then Ctrl+Alt+F7 and login _as yourself_.

NOTE: This will reset all your Desktop "Experience" (aka panels, etc) to defaults.

Please let us know.

---

### Post by Roflcopterofl on 2013-02-27
Thank you both for your help. I have created a new user account and  and I deleted the configs like you said. The issue still occurred (even on the login screen). 

After a small bit of research I found someone else with the exact same issue:

[http://ubuntuforums.org/showthread.php?t=2087795](http://ubuntuforums.org/showthread.php?t=2087795)

The black box (like a said as small as a on screen character) blink when I move my mouse. The TTYs are pretty much broken.

---

### Post by matt_symes on 2013-02-27
Hi

I think it's a bug. Raise a bug on launchpad or see if someone else has and add yourself as an affected user.

It will increase the heat on the bug.

Unless anybody here has exactly the same issue as you then you are unlikely to find a fix here. 

It does sound like a race condition but i may be wrong.

That's my feeling on the matter anyway.

Kind regards

---

