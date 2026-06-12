---
title: "Execute command after no user input for specified time"
date: 2013-01-09
forum: General Help
---

### Post by mercury1981 on 2013-01-09
Hi!

I'm currently trying to create a script to do the following:
After my computer is idle for 3 minutes (= no user input using Mouse / Keyboard) I would like to start a service (as root).

Optional: As soon as there is user input stop the service.

I would like to create this as a workaround to the broken idle-detection-functionality for BOINC.

Pseudo-Code:
```
IF no-user-input THEN execute "sudo service boinc-client start"
```Can anybody please give me hints on how to accomplish this?

Thanks a lot!

---

### Post by mercury1981 on 2013-01-10
Nobody an idea?

---

### Post by steeldriver on 2013-01-10
a bit of googling suggests people have done that kind of thing in the past by tapping into the screensaver signals - maybe that's a possibility?

[https://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions#Is_there_a_way_to_perform_actions_when_the_screensaver_activates_or_deactivates.3F_Or_when_the_session_becomes_idle.3F](https://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions#Is_there_a_way_to_perform_actions_when_the_screensaver_activates_or_deactivates.3F_Or_when_the_session_becomes_idle.3F)

---

### Post by Cheesemill on 2013-01-10
Any reason you cant just run boinc all the time but just at a lower priority than everything else. This way any action that a user does will take precedence and boinc will only use spare CPU cycles instead of intruding on other processes.

I run folding@home on my machine like this and there is no perceived difference in performance by having my CPU constantly at 100%.

---

### Post by mercury1981 on 2013-01-11
@[steeldriver]("http://ubuntuforums.org/member.php?u=1627500"): Thanks I will try this
@Cheesemill: Yes, because I want it to use GPU also and to run on 100% CPU, which is both not possible with low prio

---

### Post by mercury1981 on 2013-01-11
I tried it with the following script now:

[http://unix.stackexchange.com/questions/28181/run-script-on-screen-lock-unlock](http://unix.stackexchange.com/questions/28181/run-script-on-screen-lock-unlock)

But my problem is that I need to "sudo" in order to stop / start boinc service and I'm prompted to enter the password. Is there a possibility to work around this?

Thank you for your help!

> 
dbus-monitor --session "type='signal',interface='org.gnome.ScreenSaver'" | ( while true; do read X; if echo $X | grep "boolean true" &> /dev/null; then sudo service boinc-client start; elif echo $X | grep "boolean false" &> /dev/null; then sudo service boinc-client stop; fi done )

---

### Post by mercury1981 on 2013-01-11
Sorry - found it :-) [http://maestric.com/doc/unix/ubuntu_sudo_without_password](http://maestric.com/doc/unix/ubuntu_sudo_without_password)

---

### Post by steeldriver on 2013-01-11
^^^ if I'm reading that right, you have just opened your system to passwordless sudo for ANY command - at the very least you should restrict that to the specific command you need to run i.e. something like
```
jerome ALL=(ALL) NOPASSWD: /usr/sbin/service boinc-client /sbin/start
```(not sure that's right - you may need to read the sudo docs) or find a way to run the dbus-monitor script as root so that you don't need sudo

---

### Post by mercury1981 on 2013-01-11
But only for my user, right? So I do not see a very big issue in this - or what do you think of?

---

