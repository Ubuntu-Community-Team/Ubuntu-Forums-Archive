---
title: "Black screen after log out"
date: 2019-02-07
forum: General Help
---

### Post by who93 on 2019-02-07
Hi,
I am running Ubuntu on my Lenovo T460s and the problem is that my screen is sometimes black when I try to log in after a log out. When the screen is black, nothing happens any more - no login screen, only the power LED and the audio mute LED is on - I have to hard reset my PC.
This happens, when I lock my PC and when I want to resume, the screen is black. It does not happen every time, only a few times. Suspend is off, I disabled it in the power settings. It also happens when I lock the PC on the evening and want to use it in the morning.

Following settings:
Linux t460spn 4.18.0-14-generic #15-Ubuntu SMP Mon Jan 14 09:01:02 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
Ubuntu 18.10
Lenovo T460s running in a docking station with external monitor

Where do I find error logs?

BR

---

### Post by Claus7 on 2019-02-07
Hello,

you might have tried it, yet with ubuntu 18.04, when my screen is locked, in order to go back to normal operation I do not do hard reboot, yet just pressing the power button as normal. The computer then opens to the login screen. In other words just press your power button as normal and see what you get. 

In order to see error logs you can go to: Applications->System Tools->Logs for ubuntu flashback. I guess that if you are using ubuntu/gnome shell you could type "logs" and see if they appear. If they do not, you could try installing them from synaptic package manager with the name gnome-logs.

Regards!

---

### Post by who93 on 2019-02-08
Hi,

I already tried to press the power button as normal - no effect. I also noticed that I can not turn on/off audio with the shortcuts, the audio mute led is always on. Pressing ctrl+alt+f1/f2.. does also not work. Therefore I assume, the computer crashed completely. I already did a kernel upate (now on 4.20) and in the logs I do not find anything suspicious. Please find the log (I selected ALL in the log menu) attached. I locked the computer at around 9:35. Afterwards I had to hard reset the computer

---

### Post by Claus7 on 2019-02-08
Hello,

I will focus on the errors which are:
09:36:38 gnome-shell: [26640:26640:0208/093638.813947:ERROR:CONSOLE(277)] "Failed to execute 'postMessage' on 'DOMWindow': The target origin provided ('https://www.overleaf.com') does not match the recipient window's origin ('https://www.google.at').",

I do not get any of these errors, yet I do not use gnome-shell, yet flashback.

09:25:38 sudo: pam_unix(sudo:auth): authentication failure; logname= uid=1001 euid=0 tty=/dev/pts/3 ruser=XXX rhost=  user=XXX
09:25:24 gnome-shell: pushModal: invocation of begin_modal failed

this seems to be a bug, yet I do not see any of these messages in my system...

since it is the login screen, don't you try to purge gdm and install lightdm instead? A lot of users were having problems with this, so it might be easier than what it seems. You can go to synaptic, remove gdm3 display manager and install lightdm. Reboot and log out. See if you are getting the same behavior.

Regards!

---

