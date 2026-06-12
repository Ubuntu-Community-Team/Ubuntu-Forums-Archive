---
title: "problem with Gnomad2"
date: 2005-10-16
forum: General Help
---

### Post by Thomas Kirk on 2005-10-16
i have installed Gnomad2 but whenever i run it I get an error stating that:
Could not open jukebox:
usb_set_configuration: Operation not permitted

how do i change my settings so that this operation is permitted?

i have figured out that this setting can be changed by some commands in usblib but i don't know how to do this.

any help appreciated.

---

### Post by JedTheHead on 2005-10-17
I have always had to run Gnomad2 with root permissions.. have you tried:

sudo gnomad2 

?

Hope that works for you!

Jed

---

### Post by Mugatu on 2005-11-15
I did the following:

[COLOR="Green"]sudo gedit /usr/share/applications/gnomad2.desktop[/COLOR]

and the line that says:

[COLOR="Green"]Exec=gnomad2[/COLOR]

i replaced with:

[COLOR="Green"]Exec=gksudo gnomad2[/COLOR]

so now you can click on the Gnomad2 icon in the applications menu (if you installed from a precompiled ubuntu package) and it will automatically prompt you for the root password.

---

### Post by DrMoxie on 2005-11-21
Mugatu, thanks! I had the same problem and this did the trick for me. :KS

---

### Post by noximyre on 2005-12-18
You shouldn't (have to) switch to root user. Do this instead (copied verbatim from [http://www.linuxquestions.org/questions/showthread.php?p=1184427#post1184427](http://www.linuxquestions.org/questions/showthread.php?p=1184427#post1184427)):

No, you don't have to run as root if you configure correctly your system.

You only have to copy the file **nomad.usermap** to directory **/etc/hotplug/usb**

The content of this file is:

```

# Creative Nomad Jukebox
nomadjukebox    0x0000  0x0471  0x0222  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00     0x00000000
# Creative Nomad Jukebox 2
nomadjukebox    0x0000  0x041e  0x4100  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00     0x00000000
# Creative Nomad Jukebox 3
nomadjukebox    0x0000  0x041e  0x4101  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00     0x00000000
# Creative Nomad Jukebox Zen
nomadjukebox    0x0000  0x041e  0x4108  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00     0x00000000
# Creative Nomad Jukebox Zen USB 2.0
nomadjukebox    0x0000  0x041e  0x410b  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00     0x00000000
# Creative Nomad Jukebox Zen NX
nomadjukebox    0x0000  0x041e  0x4109  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00     0x00000000
# Creative Nomad Jukebox Zen Xtra
nomadjukebox    0x0000  0x041e  0x4110  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00     0x00000000
# Dell Digital Jukebox
nomadjukebox    0x0000  0x041e  0x4111  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00     0x00000000

```

Then you have to copy the file **nomadjukebox** to directory **/etc/hotplug/usb** and do: **chmod +x nomadjukebox**

I had to change two lines on this last file, i do the following:

```

#!/bin/sh
# Lifts a plugged in nomad jukebox to user space and
# optionally runs a client program.
# Written by Linus Walleij 2004, based on the "usbcam"
# script by Nalin Dahyabhai.
DEVICEOWNER=root
DEVICEPERMS=0666
PROGRAM="cd ~; gnomad2 --display=localhost:0"

if [ "${ACTION}" = "add" ] && [ -f "${DEVICE}" ]
then
    # New code, using lock files instead of copying /dev/console permissions
    # This also works with non-gdm logins (e.g. on a virtual terminal)
    # Idea and code from Nalin Dahyabhai <nalin@redhat.com>
    if [ "x$DEVICEOWNER" = "xCONSOLE" ]
    then
        if [ -f /var/run/console.lock ]
        then
            DEVICEOWNER=`cat /var/run/console.lock`
        elif [ -f /var/lock/console.lock ]
        then
            DEVICEOWNER=`cat /var/lock/console.lock`
        else
            DEVICEOWNER=
        fi
    fi
    if [ -n "$DEVICEOWNER" ]
    then
        chmod 0000 "${DEVICE}"
        chown "${DEVICEOWNER}" "${DEVICE}"
        chmod "${DEVICEPERMS}" "${DEVICE}"
        # Then run an optional program - this does not work yet.
        # su "${CONSOLEOWNER}" -c "${PROGRAM}"
    fi
fi

```

Now, when i connect my nomad then this script change permissions to the correct file in /proc/bus/usb and all work fine.

---

