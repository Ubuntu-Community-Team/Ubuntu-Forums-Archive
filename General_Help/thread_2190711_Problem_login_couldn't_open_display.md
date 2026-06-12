---
title: "Problem login: couldn't open display"
date: 2013-11-28
forum: General Help
---

### Post by perezcarazo.david on 2013-11-28
Hello,

when I try to login, it starts to load the desktop but comes back to the login window. In xsession-errors it is said that compiz (core) couldn't open display :0.

I have been trying to install and use nvidia drivers yesterday without success, and I got the same error, but I fixed it finally, installing gdm and adding nouveau to modules. I needed to add nouveau to modules on each boot, and the reboot to get access.
Today I tried to go back to lightdm using reconfigure, and now I can't get access anymore with my user.

I know there are a lot of similar threads with similar problems, but no solution worked for me.

System info:
- Ubuntu 12.04LTS
- Asus n61jv
- nvidia 325M
-gdm and lightdm installed.

[COLOR=#000000]I have done the following:[/COLOR]
[COLOR=#000000]- Deleted .Xauthority[/COLOR]
[COLOR=#000000]- deleted xorg.conf[/COLOR]
[COLOR=#000000]- reconfigure gdm[/COLOR]
[COLOR=#000000]- deleted everything about nvidia and installed ubuntu --> basic nvidia-common[/COLOR]
[COLOR=#000000]- added to modules nouveau[/COLOR]
[COLOR=#000000]- checked permissions on $HOME[/COLOR]
[COLOR=#000000]- checked sudoers, but there is no such line defaults as it is said in the thread, only 2 different deffaults which I 
didn't touch
[/COLOR]- tried to access with ubuntu-2d

Thanks!

---

### Post by steeldriver on 2013-11-28
Hello and welcome to the forum

Could you post at least a brief description of the things you already tried? just to save going over old ground

---

### Post by perezcarazo.david on 2013-11-28
Sure,

I have done the following:
- Deleted .Xauthority
- deleted xorg.conf
- reconfigure gdm
- deleted everything about nvidia and installed ubuntu --> basic nvidia-common
- added to modules nouveau
- checked permissions on $HOME
- checked sudoers, but there is no such line defaults as it is said in the thread, only 2 different deffaults which I didn't touch

Maybe I tried something else, but this is all as far as I remember

---

### Post by steeldriver on 2013-11-28
Apart from not being able to log in as 'user', did the reconfigure get you back to a working lightdm (i.e. you get the regular lightdm greeter screen?). Can you login via lightdm to a guest account? If you create a new user (using adduser from a virtual terminal) can that user log in via lightdm?

---

### Post by perezcarazo.david on 2013-11-28
Yes, I get the screen and everything.
I just tried to create an user and it works fine too, via lightdm and gdm.

---

### Post by steeldriver on 2013-11-28
OK so it definitely sounds like something corrupted or amiss in only that user profile - these things can be tricky to track down, apart from the .Xauthority and .ICEauthority things I've heard of people having trouble with a ~/.config/monitors.xml file. You could also temporarily rename the ~/.config directory (or less drastically, ~/.config/compiz). Another thing to try is starting a different session e.g. ubuntu-2d instead of the regular compiz-based ubuntu session

---

### Post by perezcarazo.david on 2013-11-28
OK, I gonna rename that file and later the directory.

I also tried to log in with 2d, but the same problem.

---

### Post by perezcarazo.david on 2013-11-28
**** yeah

I renamed monitors.xml and it works perfectly, and after rebooting too.

Thank you very much :D

---

### Post by steeldriver on 2013-11-28
OK that's good

---

