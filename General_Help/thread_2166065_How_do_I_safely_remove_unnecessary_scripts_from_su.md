---
title: "How do I safely remove unnecessary scripts from sudoers file?"
date: 2013-08-07
forum: General Help
---

### Post by ginger3 on 2013-08-07
Since the Jupiter Hardware and Power Management Applet is no longer being developed for Ubuntu since 13.04, I wonder how I can safely remove

```
#includedir /etc/sudoers.d
%jupiter ALL=NOPASSWD: /usr/lib/jupiter/scripts/bluetooth, /usr/lib/jupiter/scripts/camera, /usr/lib/jupiter/scripts/cpu-control, 
/usr/lib/jupiter/scripts/resolutions, /usr/lib/jupiter/scripts/rotate, /usr/lib/jupiter/scripts/touchpad, /usr/lib/jupiter/scripts/vga-out,
/usr/lib/jupiter/scripts/wifi

```

from the /etc/sudoers file?

and how do i remove jupiter from groups?

Thanks.

---

### Post by oldos2er on 2013-08-07
Did you create a backup copy of /etc/sudoers? Here's a default sudoers file: ```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset,insults
Defaults    mail_badpass
Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

```

Use ```
sudo visudo
``` to make any changes.

To delete a group: ```
sudo -i

groupdel <group>
```

Edit: I lied, "insults" isn't in the default sudoers file. I just put it in there for fun.

---

### Post by oldos2er on 2013-08-07
Edit: I lied, "insults" isn't in the default sudoers file. I just put it in there for fun.

---

### Post by ginger3 on 2013-08-07
Thank you!

---

