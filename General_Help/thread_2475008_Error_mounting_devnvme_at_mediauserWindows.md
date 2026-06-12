---
title: "Error mounting dev/nvme at media/*user*/Windows"
date: 2022-05-13
forum: General Help
---

### Post by noob-senior on 2022-05-13
Hi folks, I can't access my Windows partition anymore since a couple of days. I already tried rebooting Windows (boot to Windows -> reboot -> log in on Ubuntu) but nothing helped.

Here a screen with the error message:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290445&stc=1[/IMG]

Thanks in advance for any help.

---

### Post by oldfred on 2022-05-13
Please only attach screen shots or photos.
Easy to attach with Forum's Go Advanced editor and paper clip icon.

Windows updates often turn fast start up/hibernation back on.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by noob-senior on 2022-05-13
Thanks for your help! I managed to find out what the problem was and it happened to be a missing package (ntfs-3g). Dunno why it got lost though, but now everything works. Thanks again and have a nice day.

---

