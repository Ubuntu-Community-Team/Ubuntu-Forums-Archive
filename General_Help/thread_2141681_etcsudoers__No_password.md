---
title: "/etc/sudoers  No password"
date: 2013-05-03
forum: General Help
---

### Post by UserJB on 2013-05-03
How can I modify the /etc/sudoers file so that I don't have to type my password every time I run an sudo command?  I tried to do this myself, but got the syntax wrong and this prevented all sudo commands (I booted into another OS and restored the old sudoers file). What's the correct way to do this?

Also, how can I set a root password?

---

### Post by SlugSlug on 2013-05-03
Add 

USERNAME ALL=(ALL) NOPASSWD: ALL```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

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
USERNAME ALL=(ALL) NOPASSWD: ALL
```

---

### Post by UserJB on 2013-05-03
I added that line and immediately did a 'sudo ls' and it asked for my password.

EDIT: Nevermind.  Changed USERNAME to my username (duh!) and it worked.  Thank you.

---

### Post by Lars Noodén on 2013-05-03
You can also use [sudoers](http://manpages.ubuntu.com/manpages/raring/en/man5/sudoers.5.html) to set the timeout for a longer duration or even set it not to timeout:

```

Defaults  timestamp_timeout=-1

```

---

