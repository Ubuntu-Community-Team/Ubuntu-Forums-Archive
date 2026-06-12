---
title: "Disable automounting of USB drives with a command?"
date: 2008-03-28
forum: General Help
---

### Post by Gerlads Mod on 2008-03-28
I know I can click System -> Preferences -> Removable drives and media -> {uncheck} mount removable drives when hot-plugged.
But I don't want to use that in my case.

Is there a way to see if automounting is enabled through a command?
And is there a command to disable/enable automounting with a command.


Thanks.

---

### Post by Xyhthyx on 2008-03-28
Gnome volume manager uses gconf for its settings, so in order to do it you'll be using gconf through the command line. Here's how to do it:


For automount removable drives, use the following (change "true" to "false" to turn it off and vice versa):
```

gconftool-2 --type bool --set /desktop/gnome/volume_manager/automount_drives true

```

For automount media drives, use the following (change "true" to "false" to turn it off and vice versa):
```

gconftool-2 --type bool --set /desktop/gnome/volume_manager/automount_media true

```

Edit: Look in the gconf-editor under /desktop/gnome/volume_manager for all of it's options and follow the examples above to change them via the command line.

---

### Post by Gerlads Mod on 2008-03-28
I was really hoping that there would be a command that would work in all distro's and desktop environments.

See I'm writing a shell script and it needs to work with most distro's. So I need a command that will work.

I may have to look at an alternative.

---

### Post by cdenley on 2008-03-28
Automounting is handled by the desktop environment, and is even handled and configured differently on hardy, so there isn't going to be a universal way.

---

### Post by Gerlads Mod on 2008-03-28
That really sucks.

Is there a way to check if a device is mounted with a command?
Something like:
```

if [ $USB = mounted ]
then
      mounted=true
else
      mounted=false
fi

```
I know **mount** works but that displays everything.

---

### Post by cdenley on 2008-03-28
Yeah, I wasn't happy with the change in hardy. Sort of messes up my program.

You can see if a device is mounted very easily
```

#!/bin/bash
cat /etc/mtab|grep $1>/dev/null
if [ $? = 0 ]
then
        echo mounted
else
        echo not mounted
fi

```
where $1 is the path to the device.

---

### Post by Gerlads Mod on 2008-03-28
Thanks man that will work just fine.

---

### Post by xixsixxix on 2008-04-28
> **cdenley said:**
> Automounting is handled by the desktop environment, and is even handled and configured differently on hardy, so there isn't going to be a universal way.

A quick note for anyone wanting to use the aforementioned gconftool-2 method -- for 8.04 Hardy you'll want to set /apps/nautilus/preferences/media_automount

Example (disable automounting):
```
$ gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount false
```

Hope that helps someone =)

---

