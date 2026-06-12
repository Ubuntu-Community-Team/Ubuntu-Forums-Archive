---
title: "Debconf error after installing ActivePerl"
date: 2006-07-24
forum: General Help
---

### Post by elamericano on 2006-07-24
I've install ActivePerl, and it is working fine. /usr/bin/perl is now a symlink to /opt/ActivePerl-5.8/bin/perl. The only problem is that every apt install now gives me an error, because debconf/log.pm is not found.

I can't find log.pm anywhere on my system, and log.pm on the net is too generic. Does anyone know how to fix this error? I don't know if it's messing up my installs or if only logging is affected - maybe I only need to silence the error.

---

### Post by elamericano on 2006-07-26
I have it working after setting:

export PERLLIB="/etc/perl:/usr/lib/perl5:/usr/share/perl5:/usr/local/lib/site_perl"

in /etc/X11/Xsession.d/55gnome-session_gnomerc. There has got to be a better place with all those many /etc config files, but for all X sessions I chose this.

I also set it in /etc/bash.bashrc for non-login shells. I'd have prefered to hard code it in activeperl rather than figure out how Ubuntu sets up environment variables, but I couldn't find exactly where to do that.

Feel free to comment if I can improve this, 'cause I didn't like it 100%. Installs have stopped throwing errors though, which is good.

---

