---
title: "Why won't this acpi event work?"
date: 2013-10-28
forum: General Help
---

### Post by josephellengar2 on 2013-10-28
Hi there! I have this trouble with my laptop where when I suspend it, the wireless and wired internet drivers are not properly reloaded. I fixed this by making pm-utils unload the drivers at suspend and reload them at resume, but this caused another problem.

Closing the laptop lid does not use pm-utils to suspend, so I am trying to use acpi events to make this work.

So far I have the following:

Under events I have this file:

```

# /etc/acpi/events/laptop-lid-close
# This is called when the user closes the laptop lid and calls
# pm-suspend so wireless will work

event=button/lid
action=/etc/acpi/lidclose.sh

```

And then under /etc/lidclose.sh I have this (it is executable):

```

#!/bin/sh

pm-suspend &

```

However, it still doesn't work. I can't tell what the computer is using to suspend (dbus maybe?) but it's definitely not pm-utils. When I run pm-suspend myself, the drivers are reloaded properly, but when I close the lid, it's not. Any suggestions?

Thanks!

---

### Post by marcinkowski on 2013-10-28
You might want to try the solution posted here:

[http://ubuntuforums.org/showthread.php?t=2182128&p=12830153#post12830153](http://ubuntuforums.org/showthread.php?t=2182128&p=12830153#post12830153)

It solved the wifi after suspend issue for me, though I am still experiencing another suspend issue ([http://ubuntuforums.org/showthread.php?t=2184159](http://ubuntuforums.org/showthread.php?t=2184159)).

---

### Post by josephellengar2 on 2013-10-28
Thanks, but I already solved the wifi after suspend issue. The issue that I am facing right now is different. It's getting the computer to suspend when the lid is closed. See my first post.

---

### Post by Toz on 2013-10-29
A couple of suggestions.

1. If you are using 13.10, edit the file **/etc/systemd/logind.conf** and change the line:
> #HandleLidSwitch=suspend
...to read:
```
HandleLidSwitch=ignore
```
...in 13.10, it looks like systemd is managing the lid close event.

2. Your **llidclose.sh** file should be saved in /etc/acpi (not sure if that was a typo in your initial post). I would also remove the "&" from the pm-suspend command and add the full path so that it reads:
```
#!/bin/sh
/usr/sbin/pm-suspend
```

3. Be sure that acpi is emiting the "button/lid" event when you close the lid. To check, in a terminal window, run:
```
acpi_listen
```
...close the lid and re-open it and look for the event to be listed.

You'll need to reboot for #1 to take effect or reload acpid for only #2 to take effect.

---

### Post by josephellengar2 on 2013-10-29
Thanks Toz! Worked great. I'm marking this solved.

---

