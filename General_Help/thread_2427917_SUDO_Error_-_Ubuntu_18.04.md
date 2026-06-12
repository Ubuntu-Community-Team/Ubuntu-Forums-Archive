---
title: "SUDO Error - Ubuntu 18.04"
date: 2019-09-27
forum: General Help
---

### Post by andybell79 on 2019-09-27
Hi,

I was trying to stop SUDO asking for a pasword everytime I do something but I'm now seeing the below error when trying to do anything in Termainal using SUDO:

>>> /etc/sudoers: syntax error near line 32 <<<
sudo: parse error in /etc/sudoers near line 32
sudo: no valid sudoers sources found, quitting...
sudo: unable to initialise policy plug-in

Is there any way round it or would I need to do a fresh install?

Thanks in advance for any help.

Andy.

---

### Post by ajgreeny on 2019-09-27
Difficult to say without seeing what you have done to make those changes.

I presume you must have edited the /etc/sudoers file, so how did you edit that file when you made those changes, and what changes were made; do you have a backup copy of the sudoers file that you changed?

The /etc/sudoers file is a very important part of the whole admin/sudo system, and it is a file that should only be edited using the ***sudo visudo*** command as that will open the file as root, and most importantly, will check the syntax before saving the new version.

If you have a backup copy you could restore that version and all should be OK again.
If you have no backup copy you could find a copy in the live system you used to install the OS originally, and failing that save the file I show below (my sudoers file) and replace your version with this one.
```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults        mail_badpass
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
#
```

---

### Post by andybell79 on 2019-09-27
Thanks,  not sure why I didn't think of the backup!  I do have one I thing from before I changed the file.

I'll check though, thanks again.

---

