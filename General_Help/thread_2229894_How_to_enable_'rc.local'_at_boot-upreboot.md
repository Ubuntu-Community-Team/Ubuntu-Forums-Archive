---
title: "How to enable 'rc.local' at boot-up/reboot?"
date: 2014-06-15
forum: General Help
---

### Post by revigor5 on 2014-06-15
I need to execute something at bootup/reboot, but apparently **rc.local** is not enabled.
Here's my rc.local setup:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
# The following for logkeys 
#
#
# Edited with VI 
#
logkeys --start --keymap=/home/revigor/Documents/Custom.map --output /home/revigor/Documents/COMP-errors.log --device=/dev/input/event3
exit 0
```

---

### Post by brantcgardner on 2014-06-16
I think you'll find that rc.local is enabled but your command isn't executing the way you are expecting.  To rule this out, add a line like this to your rc.local...

```

echo Test > /home/revigor/test.fil

```

...then reboot and see if you have that file in your user directory.

I've done similar tasks to turn on keyboard lights, etc. and what it turned out to be for me was that X needed to be running for the command I was trying to use.  Perhaps something similar is needed in your case.

---

### Post by revigor5 on 2014-06-16
I just tried that, no avail.. Could it be that since my home directory is encrypted, the command won't execute on boot?

**EDIT: ****Just removed home directory encryption on my account, rc.local now executes successfully.**

---

