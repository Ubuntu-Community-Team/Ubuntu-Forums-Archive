---
title: "USB Keyboard not Working in Ubuntu"
date: 2008-06-25
forum: General Help
---

### Post by webbed on 2008-06-25
I have had a bit of a look through some of the posts here but have been unable to find a solution to my problem which started yesterday.

My Microsoft Natural® Ergonomic Keyboard 4000 is unusable once I reach the Ubuntu Login Screen it works in the Bios, Grub and even on the Windows Vista part of my machine but not Ubuntu.

Plugging in a PS/2 Keyboard works straight away. I have tried:

Rebooting
Pressing a few of the keys and waiting 15 secs
Disconnect/Reconnect Keyboard at GDM screen
Disconnect/Reconnect Keyboard while logged in

Looking through the gnome-device-manager it has detected that my keyboard is attached and even the logs show the device disconnecting and reconnecting.

Usually around 5% or less of the time this issue would arrise at the login screen I would simply reboot but then it would work.

The only changes made to my installation yesterday was an upgrade of the Linux Kernal (which stopped by Compiz desktop effects from workins) and I had to use recovery mode to go back to no desktop effect and reconfigure and reinstall NVIDIA drivers. This then required a reboot which allowed me to boot up and login using the USB keyboard.

Any help would be greatly appreciated.

---

### Post by webbed on 2008-06-25
Issue has been resolved, I remembered that I had also installed Putty and the VisualBoyAdvance emulator once these programs were removed I disconnect and reconnected the keyboard and it worked straight away.

A PS/2 keyboard was able to work when the USB did not, still not sure why though.

---

### Post by webbed on 2008-07-11
The issue has reappeared again as I mentioned before it happens occasionally.

I look through the Gnome Device Manager and found the error that this "USB Device does not have enough power to operate".

Which is strange because it usually works fine, I tried unplugging and reconnecting it a few times with the same message.

Left it out for 5 mins and plugged it back in and it worked again.

The only USB devices plugged in are an externally power HDD, the keyboard in question and a USB mouse.

---

### Post by SirLaffALot on 2009-06-09
I'm having a similar problem: every few logins my USB keyboard and/or USB trackball don't work.  This also frequently happens when I haven't used the PC for 15 minutes or so; I lose my mouse function, even though it worked just minutes before.

I'm a complete newbie, just installed Jaunty on laptop and desktop within the past few weeks.  Anyone have a hint or suggestion?

---

