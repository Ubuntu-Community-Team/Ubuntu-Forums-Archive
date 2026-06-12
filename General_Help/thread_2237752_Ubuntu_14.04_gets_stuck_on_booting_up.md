---
title: "Ubuntu 14.04 gets stuck on booting up"
date: 2014-08-03
forum: General Help
---

### Post by OriTheEep on 2014-08-03
After several attempts at installing 14.04 (problems mostly caused by irritatingly 32 bit Skype and 32 bit Wine, both of which are needed) I finally got it mostly working. The machine is running permanently (Gnome Flashback metacity) so I have no idea which or even if an update caused this but the machine now will not reboot, being stuck at the screen with the changing coloured dots.

Network shares are usable by other machines despite the "Starting SMB/CIFS File and Active Directory Server" fail error message, displayed on pressing [ESC]. The last message shown on this screen is "Stopping anac(h)ronistic cron", this having been started with the previous message.

Presumably a bootlog.txt will be useful? It does seem to be customary. Unfortunately I don't know nor could I find out wherein it lies and nautilus failed to find it searching on another computer. Might explain why some people take photographs of their screens.

Reinstalling again is not an option as the hard disc is now fully populated and I couldn't get it partitioned during install or get it installed after partitioning. I'm saving up for a backup drive, poor impecunious bunny that I am.

---

### Post by OriTheEep on 2014-08-04
Aha! The file in question goes under the name "boot.log" and lives in /var/log. The trouble is that this is overwritten at each boot and to get to it, I need to reboot, summon the Grub menu with a hold of the shift key, select a Recovery Mode option, choose to drop into a root command line and then discover that I cannot copy the required file to a shared folder as the filesystem is, apparently, read only. This may be significant?

In any case, I need the previous boot log and there doesn't appear to be a boot.old. Any ideas on that one out there?

---

