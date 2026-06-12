---
title: "Ubuntu 14.04 won't shutdown from menu (UEFI Issue too?)"
date: 2016-07-30
forum: General Help
---

### Post by rwigle on 2016-07-30
I think these two issues are related.

1. While installing a recent update (?shim-signed?) I was informed that UEFI was going to be disabled on my machine. I was asked to supply and confirm a password. Then a screen came up saying hit any key to proceed, but hitting the key just triggered Ubuntu to start normally. (No troubles apparent at the time).

2. After my session I tried to shutdown using the menu from the panel. No dice. Because I have seen some issues of slow shutdown I just left the machine... for an hour. Still no shutdown. "sudo shutdown -P now" works fine.

Other info. I have a new grub menu that says:

Ubuntu
-- Advanced options for Ubuntu
-- UEFI options (something like that)
-- System setup

If I choose the UEFI setup options I get an error message about a missing file with an extremely long file name ending in MokManager.efi (Machine returns to Grub before I can write file name down)

---

### Post by nikefalcon on 2016-07-30
Try the dbus commands given here: [https://askubuntu.com/questions/168879/shutdown-from-terminal-without-entering-password#385316](https://askubuntu.com/questions/168879/shutdown-from-terminal-without-entering-password#385316)
The error messages ought to give some indication about what's going wrong.

---

### Post by rwigle on 2016-08-01
Thanks for the suggestion. Here's the command I tried to execute followed by the error I got.

```

/usr/bin/dbus-send --system --print-reply --dest="org.freedesktop.ConsoleKit" /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.ConsoleKit was not provided by any .service files

```

I have a feeling that the two errors I have are related, since I they coincide with an update of shim-signed that didn't go according to plan.

---

