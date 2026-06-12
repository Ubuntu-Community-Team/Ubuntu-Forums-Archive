---
title: "Logon Screen Small Resolution"
date: 2008-06-17
forum: General Help
---

### Post by Dr.Dixie on 2008-06-17
Here's my situation.

1. I boot up. The screen, which can go up to a fantastic 2048x1536, runs the default Ubuntu booting screen at 1280x1024.
2. After it finishes, the logon screen eventually loads. This is where my problems start. The screen seems to show only about the top left 640x480 of the logon screen, meaning, I think, the top left quarter of the Ubuntu logo.

This is my problem. A few more details...
a) I can log on. I type in my username, enter, type in my password, then enter again. Everything loads up as normal, at the top resolution my monitor can do.

What's up with the logon screen? Why can I only see that much of it? And also, how might I change the resolution at which the boot screen comes up in?


!Dr.Dixie!

---

### Post by rraj.be on 2008-06-17
Install startupmanager
```

sudo apt-get install startupmanager

```

You can control all your startup activities including screen resolution GRUB password timeout value, Boot screen colour etc

---

### Post by Dr.Dixie on 2008-06-19
Startupmanager works without flaws. My greatest problem is still unsolved. When I enter it, the logon screen only shows the top left 640x480 of the logon screen. Help!


!Dr.Dixie!

---

### Post by louieb on 2008-06-26
New install of Hardy. Have the same problem. So heres a bump.  Don't mean to hijack you thread.

This PC is dual booting Gutsy and Hardy. GDM is fine in Gutsy.
Only see part of the login screen in Hardy.   Main problem is Sessions and options menu is off the screen.  
Once I login screen resolution is fine.

---

### Post by louieb on 2008-07-01
Got my screen fixed.  
installed **nvidia-settings**
Ran```
gksudo nvida-settings
```Set the resolution and refresh rate to my liking. 

Clicked on the button to save settings to xorg.conf.

When I restarted the logon screen is normal.

---

