---
title: "Pulling hair with Hardy"
date: 2008-04-28
forum: General Help
---

### Post by drewcoon on 2008-04-28
Hey, ever since I installed Hardy over my old Gutsy (which worked awesome, by the way), I've been experiencing tons of problems that didn't exist previously.

Whenever I plug in a usb device (like a jump drive or a camera), it used to show up on my desktop, or in the case of a camera, it started the importing program to get files from the camera. Here is what I get if I try to import photos through terminal,

```
drewc@linxp:~$ f-spot-import
libhal.c 1310 : invalid udi:  doesn't startwith '/org/freedesktop/Hal/devices/'. 
error: libhal_device_get_property_type: (null): (null)
libhal.c 1310 : invalid udi:  doesn't startwith '/org/freedesktop/Hal/devices/'. 
error: libhal_device_get_property_type: (null): (null)
libhal.c 1310 : invalid udi:  doesn't startwith '/org/freedesktop/Hal/devices/'. 
error: libhal_device_get_property_type: (null): (null)
gphoto2:usb:000,000
Starting new FSpot server

Unhandled Exception: System.Exception: Unsupported SQLite database version
  at Banshee.Database.QueuedSqliteDatabase.ProcessQueue () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
drewc@linxp:~$ 
```

This used to work fine on Gutsy, but now it won't. Anyone have a solution?

I'm also experiencing huge problems with making my Broadcom chipset wireless card work, and sporadically having massive amounts of IOwait that reminds me of Windows for some reason. But the camera issue is the one I'm tackling now. Can anyone help? Thanks in advance :)

---

