---
title: "starting system log daemon... hangs at boot"
date: 2007-11-03
forum: General Help
---

### Post by loadeddreams on 2007-11-03
I went and installed kiba-dock (along with dependencies) and my computer froze while using it.. it was slowly responsive, so I eventually got it to power down.
When I rebooted, I noticed it was hanging.. went to tty1 and could login, so I switched to tty8 (displaying bootup messages) and saw it was hanging on starting system log daemon.
I was patient and it eventually fails, so I let it keep going only to notice it is also hanging while starting samba!

I've went through and purged all the installed dependencies I installed for kiba-dock and also did a sudo make uninstall on kiba-dock and it's plugins (including dbus, etc) and did a reboot to only see the same issue yet again.

I have dug through the aptitude log to make sure there were no adverse packages installed I didn't realize, and there were none.

so now I'm lost.... I think it might have to do with hal needing to start earlier than it is... but don't see how that could have happened.
can someone post their hal defaults at boot (via /etc/rc2.d, I guess)
So it should be S**hal or something like that... 
or is there any way to rescue and reset my boot to defaults?

I'm just lost and about to bash my head in because I don't want to format/reinstall this after I've been customizing it forever and have everything about how I want it! :(

---

### Post by Pumalite on 2007-11-03
/etc/rc2.d:

README                       S20backuppc       S89anacron
S05vbesave                   S20exim4          S89atd
S10acpid                     S20hotkey-setup   S89cron
S10powernowd.early           S20makedev        S91apache2
S10sysklogd                  S20nvidia-kernel  S98usplash
S10xserver-xorg-input-wacom  S20powernowd      S99acpi-support
S11klogd                     S20rsync          S99laptop-mode
S12dbus                      S22consolekit     S99rc.local
S12hal                       S24avahi-daemon   S99rmnologin
S19cupsys                    S24dhcdbd         S99stop-readahead
S20apmd                      S25bluetooth
S20apport                    S30gdm

---

### Post by loadeddreams on 2007-11-03
unfortunately that was not it.. only difference was dbus, which I changed to S12 but didn't help.

Any ideas anyone?

---

