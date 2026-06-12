---
title: "Disabling guest account caused unexpected login problems"
date: 2012-12-04
forum: General Help
---

### Post by resander on 2012-12-04
for a 32-bit desktop PC running Ubuntu 12.04 LTS...

Followed the instructions in Ubuntu-geek: gksudo gedit /etc/lightdm/lightdm.conf, added line allow-guest=false and restarted by sudo restart lightdm.

This recipe worked for another 64-bit PC running 64-bit Ubuntu 12.04 LTS but not for the 32-bit desktop.

When doing the sudo restart the screen flickered (did it crash?) and went blank. On reboot the system displayed an alert dialog with title 'The system is running in low-graphics mode' and a message 'The screen, graphics card and input device cannot be detected correctly. You need to configure these yourself.' Clicking OK in the alert dialog brings up another dialog with 4 radio-button choices, but I did  not make any progress selecting any of these. Pressing escape key brings up the normal bootup screen with the marching dots under the 'Ubuntu' keyword, but it never stops. Doing Ctrl-Alt-Del restarts boot. Booting to recovery mode then selecting 'network' and 'root' and trying to restore by removing the allow-guest=false line did not work. Got the message 'GTK warning **: Cannot open the display' when entering the gksudo gedit /etc/lightdm/lighdm.conf command.

I booted from the Live CD 12.04.1 and display and io worked fine in 'Try Ubuntu' mode. Have complete backup on 30+ dvds, so a reinstall and data restore is going to take a long time.

What else can I try first?

Ken

---

### Post by steeldriver on 2012-12-04
You won't be able to run gedit when you're in a text-based recovery mode - try nano or vi instead

```
# nano /etc/lightdm/lightdm.conf
```You may need to remount the filesystem with write permissions first if you have not already done so

```
# mount -o remount,rw /
```

---

### Post by resander on 2012-12-05
Many thanks steeldriver,

Used the nano editor for removing the allow-guest=false line (write permission mount not needed).

On reboot the 'Guest' was back in the login accounts list.

Added the 'allow-guest=false' to /etc/lightdm/lightdm.conf again and saved the file. This time I shutdown the system in normal fashion and rebooted. That worked. The Guest item in the login dialog had gone.

I think the 'sudo restart lightdm' may have caused the problem, so best to avoid this and just shutdown and log back on.

---

