---
title: "Nautilus/Gnome Permissions"
date: 2007-09-27
forum: General Help
---

### Post by jimmywu013 on 2007-09-27
Linux noob here.
I'm a bit puzzled by the permissions Nautilus runs with - it should be as the logged in user, but sometimes it does things that I would need sudo for in the terminal.
For example, it automounts and unmounts my USB drive.  If I try to unmount in terminal, I need sudo, so why doesn't Nautilus need it?
Also, the shutdown command needs root permissions in the terminal, but the gnome-panel shutdown button apparently doesn't.
Can someone explain this to me?

Thanks.
Jimmy

---

### Post by bettlebrox on 2007-09-27
dbus & hal desktop integration allows for automounting and other things to happen:

[http://www.redhat.com/magazine/003jan05/features/dbus/#what-is](http://www.redhat.com/magazine/003jan05/features/dbus/#what-is)

[INDENT]The gnome-volume-manager daemon is a policy daemon that runs in the session and whose sole purpose in life is to detect when media is added that the user can use. Such media include USB thumb drives, cameras, flash cards, blank CD-Rs, and audio CDs. Based on user configured policy, certain actions are taken depending on the type of media. For mass storage devices such as thumb drives, the media is mounted. Blank CD-Rs pop up the Nautilus CD burner, cameras invoke a photo viewing application, and audio CDs start up the CD player. It does this by watching for device added and device removed D-BUS signals from HAL and invoking policy code if a device which it cares about changes state.[/INDENT]

---

### Post by Wolki on 2007-09-27
> **jimmywu013 said:**
> For example, it automounts and unmounts my USB drive.  If I try to unmount in terminal, I need sudo, so why doesn't Nautilus need it?

Only if you use the mount command, if you use e.g. pmount, you don't need superuser rights.


> Also, the shutdown command needs root permissions in the terminal, but the gnome-panel shutdown button apparently doesn't.

If I remember correctly, it doesn't use shutdown but accesses gdm, which has sufficient rights to do that (otherwise you couldn't shutdown/reboot at the login screen).

---

### Post by jimmywu013 on 2007-09-27
Thanks everyone for the replies

> **Wolki said:**
> Only if you use the mount command, if you use e.g. pmount, you don't need superuser rights.

What about fstab entries that have users option?  My understanding is that the users options allows any user to mount and unmount.  I used it for an entry for a cifs Windows share in my fstab, but I still have to sudo to mount and unmount.  Am I misunderstanding how the users (or user) option works?

> **Wolki said:**
> If I remember correctly, it doesn't use shutdown but accesses gdm, which has sufficient rights to do that (otherwise you couldn't shutdown/reboot at the login screen).

Oh, I see.  Thanks

---

