---
title: "Execute as other user from script: No tty present"
date: 2015-10-22
forum: General Help
---

### Post by Kjeldgaard on 2015-10-22
Hi,

When Transmission finishes a torrent download it executes a script as user debian-transmission. Inside this script I am attempting to execute a command as "kodi" user. I have the following code.
```
sudo -H -u kodi perl /home/scripts/MyScript.pl &> /tmp/MyScript_transmission.log
```

This does not work. In the log I find the following error: "sudo: no tty present and no askpass program specified". I have searched for solutions, and it seems I need to edit the "sudoers" file. I now have this:
```
# This file MUST be edited with the 'visudo' command as root.#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults        mail_badpass
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


#includedir /etc/sudoers.d
kodi ALL = (root) NOPASSWD: /usr/bin/perl
Defaults!/usr/bin/perl !requiretty

```

But I still see the "No tty present..." error.

The location of perl is:
```
kodi@NUC:~$ which perl/usr/bin/perl

```
I can't see what is wrong. Can someone see what I am missing?

Thanks in advance,
Kjeldgaard

---

### Post by SeijiSensei on 2015-10-23
One solution might be to put the two users into a Unix group, assign that group to any programs you need to run, and enable group-executable permissions for those programs.

---

### Post by Lars Noodén on 2015-10-23
Also, your perl script should be launched by name rather than running perl.  The first line in your script should be 

```

#!/usr/bin/perl

```

And then the script file made executable. That's the usual way.  Otherwise, the user kodi could run absolutely anything as long as it was wrapped in perl.  
Same for this situation:

```

kodi ALL = (root) NOPASSWD: /home/scripts/MyScript.pl

```

The user kodi could re-write MyScript.pl to to anything.  In order to make it safer, after you have worked out the details of what the script should do, you can move it to /usr/local/bin/ and make sure that kodi can read it but not write it:

```

kodi ALL = (root) NOPASSWD: /usr/local/bin/MyScript.pl

```

---

