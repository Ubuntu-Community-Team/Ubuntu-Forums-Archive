---
title: "LXTerminal display lag"
date: 2014-05-26
forum: General Help
---

### Post by Xyphoid on 2014-05-26
After the latest software update I have display lag whenever I drag an LXTerminal window (see pic).
This doesn't happen with other windows (Firefox, PCManFM etc.).
I tried reinstalling LXTerminal, but that didn't help.

Anybody knows what I can do about it?

---

### Post by vasa1 on 2014-05-26
What are your exact OS and DE specs and version numbers? You seem to have done a fair bit of customization. 
Have you added compositing?

Why is this in Other OS?

---

### Post by bapoumba on 2014-05-27
> **vasa1 said:**
> What are your exact OS and DE specs and version numbers? You seem to have done a fair bit of customization. 
Have you added compositing?

Why is this in Other OS?

No idea, *thread moved to **General Help**.*

---

### Post by Xyphoid on 2014-05-27
> **vasa1 said:**
> What are your exact OS and DE specs and version numbers? You seem to have done a fair bit of customization. 
Have you added compositing?

Why is this in Other OS?

I'm running Lubuntu 14.04
Kernel Linux 3.13.0-27-generic(x86_64)
LXTerminal 0.1.11

What are DE specs?

I never had this problem until two days ago. I only did an update of the system. 
Haven't installed anything new.
It only happens with LXTerminal window. All other windows are fine.

---

### Post by vasa1 on 2014-05-27
Since you're sure it's related to the "latest update", please post the content of /var/log/apt/history.log for the relevant date only (otherwise the post may get too long). That will tell people just what was in the latest update that could have caused you this problem. 

Of course, you can always create another user account just to see if the same thing happens there. If you're lucky and all is well in the other account, that should help narrow the scope.

BTW, are you using the default window manager (Openbox) and are you using some form of compositing?

---

### Post by Xyphoid on 2014-05-28
Thanks for the tips.

Here is my /var/log/apt/history.log
from when my problems began.

```
Start-Date: 2014-05-26  20:26:10
Commandline: aptdaemon role='role-commit-packages' sender=':1.33'
Install: linux-image-extra-3.13.0-27-generic:amd64 (3.13.0-27.50), linux-image-3.13.0-27-generic:amd64 (3.13.0-27.50), linux-headers-3.13.0-27-generic:amd64 (3.13.0-27.50), linux-headers-3.13.0-27:amd64 (3.13.0-27.50)
Upgrade: python3-problem-report:amd64 (2.14.1-0ubuntu3.1, 2.14.1-0ubuntu3.2), libebook-contacts-1.2-0:amd64 (3.10.4-0ubuntu1, 3.10.4-0ubuntu1.1), evolution-data-server-common:amd64 (3.10.4-0ubuntu1, 3.10.4-0ubuntu1.1), linux-headers-generic:amd64 (3.13.0.24.29, 3.13.0.27.33), python-apport:amd64 (2.14.1-0ubuntu3.1, 2.14.1-0ubuntu3.2), libsane-common:amd64 (1.0.23-3ubuntu3, 1.0.23-3ubuntu3.1), pidgin-data:amd64 (2.10.9-0ubuntu3, 2.10.9-0ubuntu3.1), libcgmanager0:amd64 (0.24-0ubuntu5, 0.24-0ubuntu6), libcgmanager0:i386 (0.24-0ubuntu5, 0.24-0ubuntu6), python-problem-report:amd64 (2.14.1-0ubuntu3.1, 2.14.1-0ubuntu3.2), gtk2-engines-pixbuf:amd64 (2.24.23-0ubuntu1, 2.24.23-0ubuntu1.1), libgtk2.0-common:amd64 (2.24.23-0ubuntu1, 2.24.23-0ubuntu1.1), ifupdown:amd64 (0.7.47.2ubuntu4, 0.7.47.2ubuntu4.1), libcamel-1.2-45:amd64 (3.10.4-0ubuntu1, 3.10.4-0ubuntu1.1), libsane:amd64 (1.0.23-3ubuntu3, 1.0.23-3ubuntu3.1), libsane:i386 (1.0.23-3ubuntu3, 1.0.23-3ubuntu3.1), libpurple0:amd64 (2.10.9-0ubuntu3, 2.10.9-0ubuntu3.1), openssh-client:amd64 (6.6p1-2ubuntu1, 6.6p1-2ubuntu2), ltrace:amd64 (0.7.3-4ubuntu5, 0.7.3-4ubuntu5.1), libsdl1.2debian:amd64 (1.2.15-8ubuntu1, 1.2.15-8ubuntu1.1), libgtk2.0-0:amd64 (2.24.23-0ubuntu1, 2.24.23-0ubuntu1.1), apport-gtk:amd64 (2.14.1-0ubuntu3.1, 2.14.1-0ubuntu3.2), apport:amd64 (2.14.1-0ubuntu3.1, 2.14.1-0ubuntu3.2), libedataserver-1.2-18:amd64 (3.10.4-0ubuntu1, 3.10.4-0ubuntu1.1), python3-apport:amd64 (2.14.1-0ubuntu3.1, 2.14.1-0ubuntu3.2), linux-libc-dev:amd64 (3.13.0-24.47, 3.13.0-27.50), locales:amd64 (2.13+git20120306-12, 2.13+git20120306-12.1), linux-image-generic:amd64 (3.13.0.24.29, 3.13.0.27.33), pidgin:amd64 (2.10.9-0ubuntu3, 2.10.9-0ubuntu3.1), linux-generic:amd64 (3.13.0.24.29, 3.13.0.27.33)
End-Date: 2014-05-26  20:29:11

Start-Date: 2014-05-26  20:53:05
Commandline: /usr/sbin/synaptic
Reinstall: lxterminal:amd64 (0.1.11-4ubuntu3)
End-Date: 2014-05-26  20:53:19

Start-Date: 2014-05-28  01:26:24
Commandline: aptdaemon role='role-commit-packages' sender=':1.31'
Upgrade: gstreamer1.0-plugins-bad-faad:amd64 (1.2.3-1ubuntu2, 1.2.4-1~ubuntu1), gstreamer1.0-plugins-bad:amd64 (1.2.3-1ubuntu2, 1.2.4-1~ubuntu1), libgstreamer-plugins-good1.0-0:amd64 (1.2.3-1ubuntu2, 1.2.4-1~ubuntu1), gstreamer1.0-plugins-good:amd64 (1.2.3-1ubuntu2, 1.2.4-1~ubuntu1), gstreamer1.0-plugins-bad-videoparsers:amd64 (1.2.3-1ubuntu2, 1.2.4-1~ubuntu1), libgstreamer-plugins-bad1.0-0:amd64 (1.2.3-1ubuntu2, 1.2.4-1~ubuntu1)
End-Date: 2014-05-28  01:26:37
```

I am using the default window manager (Openbox) and not using compositing.
I just changed the theme and window borders. Tried to change it back, but that doesn't solve the problem.
Gonna try to create another account and test now.

- Edit -
Created a new user and the problem does not occur in that account. Where do I start looking now?

- Edit 2 -
Restored the default theme with Openbox Configuration Manager, instead of Customize Look and Feel.
Why are there two ways to change themes and window borders?

After I change the theme, the problem is gone. But when I reopen LXTerminal, the problem is back again.

---

### Post by vasa1 on 2014-05-28
Just saw you edit.

So that means there's some configuration or theme problem originating in your /home folder. 

Do you have the problem with the default theme?

Do you have a .themes folder in your home?

---

### Post by vasa1 on 2014-05-28
What are the contents of ~/.config/lxterminal/lxterminal.conf ? Maybe something's messed up there?

---

### Post by vasa1 on 2014-05-28
> **Xyphoid said:**
> ...
- Edit 2 -
Restored the default theme with Openbox Configuration Manager, instead of Customize Look and Feel.
Why are there two ways to change themes and window borders?

After I change the theme, the problem is gone. But when I reopen LXTerminal, the problem is back again.

They are two separate things. The gtk (or widget theme) affects most of the appearance of any application. The obconfig manager controls the appearance of the title bar, the position of the min/max/close buttons, the width and color of the border of each application (collectively termed window decoration, IIRC).

I don't understand this: *After I change the theme, the problem is gone. But when I reopen LXTerminal, the problem is back again.* The problem is only with LXTerminal? So after changing the theme, the first time it works fine, the next time it doesn't?

Do you have the problem with the default gtk and openbox themes? From the image you posted in the first post, you've got some non-standard theme, correct?

---

### Post by Xyphoid on 2014-05-28
> **vasa1 said:**
> What are the contents of ~/.config/lxterminal/lxterminal.conf ? Maybe something's messed up there?
Do you have the problem with the default theme?
Do you have a .themes folder in your home? 
I don't understand this: After I change the theme, the problem is gone. But when I reopen LXTerminal, the problem is back again. The problem is only with LXTerminal? So after changing the theme, the first time it works fine, the next time it doesn't?

Do you have the problem with the default gtk and openbox themes? From the image you posted in the first post, you've got some non-standard theme, correct? 



```
[general]
fontname=Monospace 10
selchars=-A-Za-z0-9,./?%&#:_
scrollback=1000
bgcolor=#000000000000
bgalpha=56026
fgcolor=#00009c13066d
disallowbold=false
cursorblinks=false
cursorunderline=false
audiblebell=false
tabpos=top
hidescrollbar=false
hidemenubar=false
hideclosebutton=false
disablef10=false
disablealt=false
```

Haven't changed anything in here.

Problem also exists with default theme.
I have a .themes folder, but it only contains one theme folder.

When I open LXTerminal (problem is only with LXTerminal window) and change the theme, the problem is gone.
But when I open a new LXTerminal window, the problem is back.

---

### Post by Xyphoid on 2014-05-28
It's not LXTerminal.config
In my testaccount where the problem does not exist, the file is the same.

Is there a way to reset all settings?

---

### Post by vasa1 on 2014-05-28
Does your test account have the same contents of ~/.themes?

---

### Post by Xyphoid on 2014-05-28
Deinstalled LXTerminal and deleted LXTerminal.conf. Reinstalled, but did't work.

---

### Post by Xyphoid on 2014-05-28
My testaccount doesn't have a .theme folder.
I deleted the .themes folder of my problem account, but that doesn't help.
Aaaaarrgghh, I'm about to loose it!! :P
It's easier to use another terminal application, but I just want to solve this.

---

### Post by Xyphoid on 2014-05-28
Found something new.
When I open LXTerminal and resize the window (or minimize it), the problem does not occur. 
But if I open LXTerminal and move it without resizing or minimizing, the problem occurs.

- Edit -
Ah, I see that in my testaccount, there are no shadows around my windows, whereas in my problemaccount there are shadows.
Can't remember I enabled this somewhere...

- Edit 2 -
Aha!!!!!
Removed xcompmgr from autostart and no more problems.
But it is still strange it only causes problems with LXTerminal.

[Crunchbang forum]("http://crunchbang.org/forums/viewtopic.php?pid=93322#p93322") with the same problem

Guess I have to choose:
LXTerminal with transparency and trailingproblem, but all other windows with shadow
or
All windows without shadow and no transparency

I go with option one.
Thanks for your help, Vasa1!

---

### Post by bapoumba on 2014-05-28
Please mark your thread as solved (under Thread tools), thanks :)

---

### Post by Xyphoid on 2014-05-28
It's not quite solved, but because of a lack of solutions and I found a workaround, I'll mark it as solved :P

---

### Post by vasa1 on 2014-05-28
> **Xyphoid said:**
> ..., whereas in my problemaccount there are shadows.
Can't remember I enabled this somewhere...

- Edit 2 -
Aha!!!!!
Removed xcompmgr from autostart and no more problems.
But it is still strange it only causes problems with LXTerminal.
...
So you did have compositing enabled. That's what xcompmgr is all about. And it's possible that you had a per-application transparency/shadow effect.

Anyway, I stay away from compositing because I haven't yet seen the need for it and my laptop is quite modest in specs. So I can't really help you any further. But I've read that [compton]("ubuntuforums.org/showthread.php?t=2144468") is better than xcompmgr. No personal experience at all. If you're adventurous, give it a try.

---

