---
title: "bash script assistance to add in display message when rdesktop cannot connect"
date: 2014-09-13
forum: General Help
---

### Post by greavette on 2014-09-13
Hello,

I'm using ltsp screen scripts to connect an ltsp session to a virtual machine through rdesktop.  It's working very well for me but I've noticed that when the VM is turned off the ltsp screen goes black with only the mouse moving around.  If the connection is lost it seems that ltsp will try to autoconnect which is a good thing.  But when it can't connect I'd like to put up a message to tell the user that the remote desktop connection was lost and a reconnect will be attempted again....or some kind of message to that effect.  seeing a black screen with only the mouse moving will just confuse our users.

My bash fu is pretty weak...could someone point me in the right direction on what I need to do to this script to get a message to display on the screen when a connection can't be made?  Perhaps the message could be displayed for a period of time (like 1 minute) before a reconnect is tried again?

Here is the script ltsp uses to connect using the rdesktop details from lts.conf.

```
#!/bin/sh
#
# Screen script that launches xfreerdp/rdesktop. Can be called from lts.conf
# like this:
#   SCREEN_07="xfreerdp -f --plugin rdpsnd server"
# or like this:
#   SCREEN_07="rdesktop"
#
# Copyright (c) 2011 Alkis Georgopoulos <http://alkisg.mysch.gr>
#
# This software is licensed under the GNU General Public License version 2,
# the full text of which can be found in the COPYING file.

. /usr/share/ltsp/screen-x-common
# xfreerdp segfaults if HOME is unset.
export HOME=${HOME:-/root}

# The same screen script can be used for rdesktop too, by just symlinking
# screen.d/rdesktop to screen.d/xfreerdp.
basename=${0##*/}

if ! type $basename >/dev/null 2>&1; then
    echo "$basename couldn't be found."
    if [ "$basename" = "rdesktop" ]; then
        echo "Some distributions have now switched to 'xfreerdp' instead of 'rdesktop'."
        echo "You may want to change your SCREEN_XX entry to that instead."
        echo "Please note that RDP_OPTIONS will need updating for xfreerdp."
    fi
    read nothing
    exit 1
fi

# Make XINITRC_DAEMON default to "True", to prevent X from restarting after
# logout. If you don't want that, force XINITRC_DAEMON=False in lts.conf.
export XINITRC_DAEMON="${XINITRC_DAEMON-True}"

# If no parameters were passed, set some reasonable defaults.
if [ $# -eq 0 ]; then
    RDP_OPTIONS=${RDP_OPTIONS:--f -u ''}
    RDP_SERVER=${RDP_SERVER:-server}
fi

COMMAND="$basename $* $RDP_OPTIONS $RDP_SERVER"

# The following logic is described at the top of xinitrc.
if [ -x /usr/share/ltsp/xinitrc ]; then
    exec xinit /usr/share/ltsp/xinitrc "$COMMAND" -- "$DISPLAY" "vt${TTY}" $X_ARGS >/dev/null
else
    eval "exec xinit $COMMAND -- $DISPLAY vt${TTY} $X_ARGS >/dev/null"
fi
```

---

### Post by greavette on 2014-09-13
Digging a little deeper I found this webpage ([https://help.ubuntu.com/community/UbuntuLTSP/RdesktopScreenScript](https://help.ubuntu.com/community/UbuntuLTSP/RdesktopScreenScript)) that says I can create a 'wrapper' I can call instead to start my rdesktop session.  I'm thinking this is maybe where I should add in my check code to see if my VM is offline.  The article I reference is very old by Internet Time (2009).  

I'm thinking of using a ping or fping do while loop in the code like this:

```
#!/bin/bash
IP='20.101.1.1'
#fping -c1 -t300 $IP 2>/dev/null 1>/dev/null
ping -c1 $IP 2>/dev/null 1>/dev/null
then
if [ "$?" = 0 ]
then
  echo "Host found"
else
  echo "Host not found"
fi
```

But I don't know how this would display in the ltsp session?  

Thoughts?

---

