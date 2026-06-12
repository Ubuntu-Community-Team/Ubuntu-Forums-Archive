---
title: "xrdp and remote desktop"
date: 2016-05-14
forum: General Help
---

### Post by shahin on 2016-05-14
I have an Ubuntu version 16.04 at my house, and am able to ssh into it form my Windows 7 machine. But remote desktop does not work. I love to fix it myself except there are so many different tutorials, and I know very little about xrdp and the configuration file /etc/xrdp.ini 
Here is what I have done so far: 

1- installed xrdp and vino 
2- Modified xrdp.ini 
3- Modified /etc/pam.d/common-session file 
4- ran the command  mate-session >~/.xsession

Here is my xrdp.ini file:

```
[globals]
bitmap_cache=yes
bitmap_compression=yes
port=3389
crypt_level=low
channel_code=1
max_bpp=24
#black=000000
#grey=d6d3ce
#dark_grey=808080
#blue=08246b
#dark_blue=08246b
#white=ffffff
#red=ff0000
#green=00ff00
#background=626c72

[xrdp1]
name=sesman-Xvnc
lib=libvnc.so
username=ask
password=ask
ip=127.0.0.1
port=ask-1

[xrdp2]
name=console
lib=libvnc.so
ip=127.0.0.1
port=5900

username=na
password=ask

[xrdp3]
name=vnc-any
lib=libvnc.so
ip=ask
port=ask5900
username=na
password=ask

[xrdp4]
name=sesman-any
lib=libvnc.so
ip=ask
port=-2
username=ask
password=ask

[xrdp5]
name=rdp-any
lib=librdp.so
ip=ask
port=ask3389

[xrdp6]
name=freerdp-any
lib=libxrdpfreerdp1.so
ip=ask
port=ask3389
username=ask
password=ask

[xrdp7]
name=sesman-X11rdp
lib=libxup.so
username=ask
password=ask
ip=127.0.0.1
port=-1
xserverbpp=24


```

```
#
# /etc/pam.d/common-session - session-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of sessions of *any* kind (both interactive and
# non-interactive).
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
session [default=1]                     pam_permit.so
# here's the fallback if no module succeeds
session requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session required                        pam_permit.so
# The pam_umask module will set the umask according to the system default in
# /etc/login.defs and user settings, solving the problem of different
# umask settings with different shells, display managers, remote sessions etc.
# See "man pam_umask".
session optional                        pam_umask.so
# and here are more per-package modules (the "Additional" block)
session required        pam_unix.so
session optional        pam_systemd.so
# end of pam-auth-update config

```

What should I look into? It just seems to be there are so many different ways and fixes for the same thing. How / where can I learn what xrdp.ini does and how to configured it so I can connect to the desktop from my win7 machine?

I have to add; when I run wireshark it seems my windows7 machine sends a reset.

---

