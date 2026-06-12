---
title: "&quot;sudo -i&quot; vs &quot;sudo su&quot;"
date: 2007-03-17
forum: General Help
---

### Post by flip314 on 2007-03-17
Is there any difference between running "sudo -i" and "sudo su"?  I've always used the -i option to sudo, though lately I've seen a lot of tutorials that mention sudoing su.  They both seem to work in all the cases I've tried them, I'm just curious if there's an actual difference.

---

### Post by Kateikyoushi on 2007-03-17
From the sudo manual.
> The -i (simulate initial login) option runs the shell specified in
           the passwd(5) entry of the user that the command is being run as.
           The command name argument given to the shell begins with a - to
           tell the shell to run as a login shell.  sudo attempts to change to
           that user&#8217;s home directory before running the shell.  It also ini&#8208;
           tializes the environment, leaving TERM unchanged, setting HOME,
           SHELL, USER, LOGNAME, and PATH, and unsetting all other environment
           variables.  Note that because the shell to use is determined before
           the sudoers file is parsed, a runas_default setting in sudoers will
           specify the user to run the shell as but will not affect which
           shell is actually run.


Actually it is like switching to root, I use it without i.

---

