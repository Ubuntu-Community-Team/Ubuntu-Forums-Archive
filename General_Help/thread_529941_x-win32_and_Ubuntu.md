---
title: "x-win32 and Ubuntu"
date: 2007-08-19
forum: General Help
---

### Post by nytrokiss on 2007-08-19
Hi 

I am having some issues running X apps on my windows computer. I am using a program called X-win32 which is supposed to enable to to run xterm over ssh on my windows desktop. However.. it seems to be completely lost! It always tells me that it cannot open the Display. So i ssh into my computer using putty.. and type in xterm i get this message.


> user@WhiteHole:~$ xterm &
xterm Xt error: Can't open display:
xterm:  DISPLAY is not set


So i was told to go into my ssh_config file and edit it.. So this is how it looks.

> 
# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
X11DisplayOffset 10
AllowX11Forwarding yes
ForwardX11 yes


Nothing works :(

Please help

Thanks
James

---

### Post by nytrokiss on 2007-08-20
Can anyone help?

---

