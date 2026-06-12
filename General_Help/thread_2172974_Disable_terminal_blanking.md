---
title: "Disable terminal blanking"
date: 2013-09-07
forum: General Help
---

### Post by hiig on 2013-09-07
I run ubuntu-server with nothing but the terminal (and byobu, but I don't think that makes a difference), and every 5 minutes or so, the terminal goes blank. I've tried using "setterm -powersave off -blank 0", but I get the error "setterm: cannot (un)set powersave mode: Inappropriate ioctl for device"

How do I work around this?

---

### Post by CaptainMark on 2013-09-07
This is not Ubuntu specific, I use Debian on my server but hopefully it should hold true for Ubuntu.
The file /etc/kbd/config contains settings for non-x screen blanking have a read through it, the settings are pretty easy to understand, the main ones you need to set are:

BLANK_TIME=0
BLANK_DPMS=off
POWERDOWN_TIME=0

Note; I also think this requires a restart to take effect

---

### Post by hiig on 2013-09-07
Found them. Do I need to do anything else, other than save the changes? Restart?

---

### Post by hiig on 2013-09-07
Okay, restarted, and it still blanks.

---

### Post by hiig on 2013-09-07
After a...very long time of searching, I found the solution:

cd /etc/default
nano grub

Find GRUB_CMDLINE_LINUX_DEFAULT and between the quotation marks, add consoleblank=0

Or, if something is already between the quotation marks, add a space after whatever is written there, and then add the above (eg. "quiet splash consoleblank=0")

Save, exit, and reboot.

(for anyone who is an absolute beginner like myself)

---

