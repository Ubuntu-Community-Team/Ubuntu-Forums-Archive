---
title: "Grub timeout of 0 stops at menu after reset button pressed"
date: 2014-02-18
forum: General Help
---

### Post by IanVaughan on 2014-02-18
Hiya,

I am setting up a headless box, so just want to configure the grub to skip pass the menu asap and continue booting.

But, although the timeout is set to 0, which works on power on and "reboot" via the command, when I press the reset button on the front panel, it shows the grub menu with no timeout, so just hangs! Not a very good state to be in for a headless box.

Here is my /etc/default/grub

```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

Of which I editted via sudo, and then ran "sudo update-grub".

---

### Post by IanVaughan on 2014-02-18
In fact, it seems to be when a boot has not completed.

Is there a file that gets written on boot complete that grub checks for?
And if so, can I tell it to not bother??

---

### Post by jeanjd63 on 2014-02-18
Hello
May be modify the file as this :
GRUB_DEFAULT=0
**GRUB_HIDDEN_TIMEOUT=0**
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

And valid by :
**sudo  update-grub**

---

### Post by coldcritter64 on 2014-02-18
> **jeanjd63 said:**
> Hello
May be modify the file as this :
GRUB_DEFAULT=0
**GRUB_HIDDEN_TIMEOUT=0**
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

And valid by :
**sudo  update-grub**

@ OP, Try this OP, but I would suggest you set a GRUB_HIDDEN_TIMEOUT= value of 3 or 4 seconds at least if you ever need to use the Shift key to bring up the menu. A value of 0 here could cause you headaches in the future if you do need to "get into" the grub menu.

As per GRUB_TIMEOUT=0, a value of 1 or higher will cause the menu to show, _*0 should be OK*_, but if the menu continues to show comment it out.

I'd suggest,
```

GRUB_DEFAULT=0
**GRUB_HIDDEN_TIMEOUT=4**
GRUB_HIDDEN_TIMEOUT_QUIET=true
**#GRUB_TIMEOUT=0**
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```And then use ```
sudo update-grub
```as jeanjd63 notes.

Cheers, coldcritter64

---

