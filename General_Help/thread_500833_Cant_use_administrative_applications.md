---
title: "Cant use administrative applications"
date: 2007-07-14
forum: General Help
---

### Post by NikoK on 2007-07-14
Just recently I have lost the ability to use administrative applications, when I try to open one (ie users and groups) the keyring window comes up transparent and the brightness of the rest of the desktop darkens....It is starting to drive me insane and almost making me want to go back to osx86....Does anyone have any idea on how this can be fixed?

If not how do I disable administrative applications needing root password...so I can run them like normal apps...because at this point I feel like it is the only solution..

---

### Post by NikoK on 2007-07-14
someone knows how cmon

---

### Post by NikoK on 2007-07-14
:(

---

### Post by NikoK on 2007-07-14
So out of the thousands of members online no one can answer this question.....

---

### Post by davidjmayo on 2007-07-14
I don't know but 3 hours is not too long to wait is it?

---

### Post by merlinus on 2007-07-14
To be clear --

Are you saying that using some of the administrative applications requires you to enter your password?

If so, is that not normal, for security purposes?

Or is it that they do not work?

-merlin

---

### Post by r0ck80y on 2007-07-14
"the keyring window" ?? Is it the password dialog box that comes up when you open an administrative application? What password are you typing, the root or the default user one?

---

### Post by Alterax on 2007-07-14
Sorry, admins must sleep too, after all.

Are you using any special desktop effects?  Beryl, Compiz, anything like that?  GKSudo seems to be running, since it  is dimming your screen.   Incorrectly configured video settings are probably the problem.

Drop to the terminal.  sudo nano /etc/X11/xorg.conf and check the video card settings.   Change the driver to vesa, save, and restart X by hitting CTRL-ALT-BACKSPACE.

--Alterax

---

### Post by NikoK on 2007-07-14
Im using beryl, it just happened as a random occurance and now its happening all the time, i changed the video driver from i810 to vesa and now I cant even log into my session because its just all white |:

---

### Post by NikoK on 2007-07-14
how awesome, can someone please reply to this and quick...im now stuck on a p3 333 |:

---

### Post by NikoK on 2007-07-15
wtf

---

### Post by merlyn on 2007-07-15
Typically there are two methods of running administrative applications in Ubuntu, either from the GUI or command line, (terminal).

In fact this applies to any application really.

However back to administration applications.

When running from either the GUI or Command line you will be prompted for a password. This is just an extra precaution to prevent people from damaging their Ubuntu install.

The password you need to provide in both cases is your normal login password.

I've attached a couple of screenshots to provide examples of the password prompt you should receive.

_**Note:**_ when running an administrative application from the command line, (terminal), you need to type "sudo" before the name of the application, (without the quotes).

Cheers.

---

### Post by Canis familiaris on 2007-07-15
Sicne you changed your graphics driver, you must also login through Metacity GNOME instead of Compiz. Just when logging go to sessions elect GNOME or Failsafe GNOME and then disable Desktop Effects.
Also your administrative problems, does your user belong to the group admin. If then log in using the username you made while you originally installed Ubuntu.
EDIT: Oh!This is not the Adminstrative problem. It seemes more of problem of Compiz.I would recommend you disable Desktop Effects a.k.a. Compiz. If you really want a 3d desktop install Beryl instead.

---

