---
title: "Error when found when loading /root/.profile: stdin: is not a tty"
date: 2015-03-26
forum: General Help
---

### Post by sterlingbutters on 2015-03-26
I received this error message after enabling graphical root login at login menu and I don't know what it means nor how to address the "problem" ("problem" because everything seems to work fine)

---

### Post by cariboo on 2015-03-26
> **sterlingbutters said:**
> I received this error message after enabling graphical root login at login menu and I don't know what it means nor how to address the "problem" ("problem" because everything seems to work fine)

Why do you want to log in as root graphically?

---

### Post by veddox on 2015-03-27
1. This thread should have been posted in a support forum, not in the Linux & OS chat.

2. The two previous posters are right: there's a reason why graphical root login is disabled by default - it's a bad idea. Apart from the security risk (any program you run will have full control over your computer), any mistake you make could have deadly consequences for your system. If you want to run a graphical application as root, the correct procedure would be:
```
ALT+F2 (this lets you enter a command in Unity)
gksudo <application>
```
Replace <application> with the name of the program you want to run. gksudo is the graphical equivalent of the commandline sudo; for technical reasons you are encouraged not to use the normal sudo to run graphical apps.

3. To get back to your original question: I don't how to fix your problem, but I can give you a brief explanation. stdin is the standard input stream; it takes text that the user inputs on the commandline and passes it on to whatever program asked for it. Usually it points to a terminal (tty), but it can be redirected to other devices, which seems to have happened here. Why or wherefore I do not know, but if you stick to the advice in point 2) you hopefully won't get the error again :-)

---

### Post by bapoumba on 2015-03-28
*Thread moved to **General Help**.*

---

### Post by fprietog on 2015-04-05
> **sterlingbutters said:**
> I received this error message after enabling graphical root login at login menu and I don't know what it means nor how to address the "problem" ("problem" because everything seems to work fine)
The problem is in /root/.profile file. At the end of that file you have:
[FONT=courier new]```
mesg n
```[/FONT]

But it doesn't works in graphical mode because (taken from man mesg) "mesg assumes that its standard input is connected to your terminal".

Change it to:
```
[FONT=courier new]if `tty -s`; then[/FONT]
[FONT=courier new]   mesg n[/FONT]
[FONT=courier new]fi[/FONT]
```

---

### Post by n.vanvliet on 2015-04-07
I got the same problem, and thanks fprietog for supplying the correct answer.

Thanks to all how pointed out that it is unsafe to login graphically as root.

You know, I love Linux. And the one of the reasons is that **I **decide how I want toconfigure the box and not some company like microsoft or cannonical.
I hope it stays this way.

BTW this should be treated as a bug, because it **assumes** a non-graphical login

Regards,
Nico

---

