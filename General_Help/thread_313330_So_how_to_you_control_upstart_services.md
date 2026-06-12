---
title: "So how to you control upstart services?"
date: 2006-12-05
forum: General Help
---

### Post by biznatch on 2006-12-05
Can someone help me out here. I've been searching for about an hour and I can't figure out how to control services from the command line in the server version of 6.10. 

I've just come over to Ubuntu from Gentoo and in there I could use rc-update. I think it was called chkconfig back in my Red Hat days.

---

### Post by jthompson on 2006-12-08
I would like to know this also.  It is a bit annoying trying to figure out what is slated to start on boot, etc.  This is all I know so far.

Apparently, the old way of doing things in 6.06 has changed.  I have read different opinions of whether or not the init scripts are the same from 6.06 to 6.10.

Anyway, I think I figured out a what to view whether or not something is slated to start at boot time.

ls -l /etc/rc?.d | grep cron

If some links show up for cron, then I think its safe to say that it will start and shutdown properly when you reboot.

Anyway, someone please enlighten us on this whole upstart thing and whether or not bum or that other tools works with it or not!!!

---

### Post by randytuggle on 2006-12-08
Have you tried SYSTEM>ADMINSTRATION>SERVICES ?

---

### Post by jthompson on 2006-12-08
I did, and I've also tried bum, but those things seem to not display all of the installed services, etc.  For instance the rsync daemon doesn't show up, but its in /etc/init.d.

Do the update-rc.d commands still apply with 6.10 Edgy?

There was a huge post on how to use bum and the text based tool (sysv-conf?), however, there is a note at the top that says many things have changed with 6.10, don't use these tools anymore...

---

### Post by fangorious on 2006-12-12
Using sysvinit, I could delete /etc/rc3.d/S13gdm and make runlevel 3 a networked, multiuser, command-line equivalent of runlevel 2. This was handy when trying to upgrade fglrx drivers. But that doesn't seem to work in edgy. The System -> Administration -> Services application doesn't give any indication that it can specify a particular runlevel, so I don't think I can use that.

---

### Post by fangorious on 2006-12-12
It just occured to me that perhaps the way to specify the runlevel at the grub menu is different in edgy than it was in dapper. In dapper, I could select a menu option and hit 'e' to enter the edit menu, then select the kernel line and hit 'e' again and then put '3' at the end of the kernel line, then hit <enter> twice and boot into runlevel 3. Is that no longer the case in edgy?

---

### Post by bheremans on 2007-01-18
I found how to do it, I modified /etc/event.d/rc-default. I needed a runlevel 3 to boot into freevo (default ubuntu is 2, single is 1) and didn't need al the other services, I added an extra kernel line in /boot/grub/menu.list with at the end "freevo" and then midified rc-default from :

```

        ............
        script
        runlevel --reboot || true

        if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
            telinit S
        elif [ -r /etc/inittab ]; then
            RL="$(sed -n -e "/^id:[0-9]*:initdefault:/{s/^id://;s/:.*//;p}" /etc/inittab || true)"
        ............

```

to :

```

        ............
        script
        runlevel --reboot || true

        if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
            telinit S
        elif grep -q -w -- "-s\|freevo\|S" /proc/cmdline; then
            telinit 3
        elif [ -r /etc/inittab ]; then
            RL="$(sed -n -e "/^id:[0-9]*:initdefault:/{s/^id://;s/:.*//;p}" /etc/inittab || true)"
        ............

```

---

