---
title: "[SOLVED] Help with sudoers settings"
date: 2008-05-31
forum: General Help
---

### Post by Zeratul021 on 2008-05-31
Hi, i'm getting a lot of trouble with correct sudoers settings. Im running 7.10 gnome and i would like to use some commands without password giving.
Let's say i got /home/me/bin folder where all my sh' are stored. And i got aliased them in .bash_aliases. What i need to do exactly if i want to run them without admin password, becasue they both have sudo in their scripts, it's network related scripts.
I got something like:

# Cmnd alias specification
Cmnd_Alias CMDS_AS_ROOT = /home/me/bin/apache2
me ALL=(ALL) NOPASSWD: CMDS_AS_ROOT

in my sudoers.

I tried a lot of option throughout the week but i cant get it working?
Thanks for any working advices or forward pointings. And please, don't copy paste link from /community here.

---

### Post by ibuclaw on 2008-05-31
Does the file save alright without errors?

If so, put the **me ALL=(ALL) NOPASSWD: CMDS_AS_ROOT** line at the bottom of the file.

As the line **%admin ALL=(ALL) ALL** will override your **NOPASSWD** option.

ie: It should look like this...
```

# Cmnd alias specification
Cmnd_Alias CMDS_AS_ROOT = /home/me/bin/apache2

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
me ALL=(ALL) NOPASSWD: CMDS_AS_ROOT

```
Regards
Iain

---

### Post by Zeratul021 on 2008-06-01
Thanks for reply,

```


# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
#%sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specificationx

# User privilege specification
root    ALL=(ALL) ALL




```

this is exactly my sudoers file, i really don't know what is going on because at mate's computer he got it working and checked mine and couldn't see whats wrong.

Regards,
Marek

---

### Post by drs305 on 2008-06-01
Did you post your entire sudoers file? It doesn't contain the two necessary lines mentioned by you and tinivole. As tinivole stated, location of the CMDS_AS_ROOT is important (_after_ '%admin ALL=(ALL) ALL'.

So your file should look like:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
#%sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specificationx

# User privilege specification
root    ALL=(ALL) ALL

# Cmnd alias specification
Cmnd_Alias CMDS_AS_ROOT = /home/me/bin/apache2

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

me ALL=(ALL) NOPASSWD: CMDS_AS_ROOT

```

You mentioned scripts. Remember that the full path/name of all commands or files (or the directory containing them) requiring root privileges must be included in sudoers. If you list a directory, NOPASSWD will only apply to the commands in that directory; the commands in subdirectories are not included by default. The file above will allow apache2, and *only* apache2 to be run as root without a password. Any other commands called by the script will not automatically run without a password.

More information can be found in 'man sudoers'.

---

### Post by Zeratul021 on 2008-06-02
Hey, sorry, that first snippet wasn't complete but i found already a problem. I didn't know that its sequential and i put both cmnd alias and nopass at the end of file. With %admin between them it seems ok.
Thanks to all for help. Once again this community has proven itself.

---

