---
title: "Getting a legal message to display upon login"
date: 2007-08-26
forum: General Help
---

### Post by wjscott on 2007-08-26
I've done a reasonably thorough scout of the forums and a cursory google search but have not so far been able to find a way to display a custom - reasonably lengthy legal message whenever any user logs on. I'm looking for something that is vaguely similar to that of XP and Vista - the OSes that I have migrated from - although I accept that there will never be identical features.

Does anyone have any idea how this is possible? Have I missed any previous explanations?


Thanks

---

### Post by kerry_s on 2007-08-26
xmessage, dialog, xdialog, etc...

i'll do a example with xmessage since i know that's installed & very simple.

gedit ~/.start-message

Your so busted

then add to startup or .Xsession>

xmessage -center -file ~/.startup-message

man xmessage <to learn more

---

### Post by kerry_s on 2007-08-26
Also for something more sophisticated, i would suggest using html & some light weight  browser, such as dillo, if you want to put links to other web sites, manual, etc... your only limited by your imagination.

---

### Post by btidwell on 2008-04-18
How exactly, does one edit the Xsession script? I am new to this and I don't want to hose my system. Is the following about right?

open terminal

type "sudo gedit /etc/X11/Xsession"

This is my printout

#!/bin/sh
#
# /etc/X11/Xsession
#
# global Xsession file -- used by display managers and xinit (startx)

# $Id: Xsession 1507M 2004-09-13 07:36:26Z (local) $

set -e

PROGNAME=Xsession

message () {
  # pretty-print messages of arbitrary length; use xmessage if it
  # is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2
  if [ -n "$DISPLAY" ] && which xmessage > /dev/null 2>&1; then
    echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} | xmessage -center -file -
  fi
}

message_nonl () {
  # pretty-print messages of arbitrary length (no trailing newline); use
  # xmessage if it is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2;
  if [ -n "$DISPLAY" ] && which xmessage > /dev/null 2>&1; then
    echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} | xmessage -center -file -
  fi
}

errormsg () {
  # exit script with error
  message "$*"
  exit 1
}

Am I in the right ballpark here?

Thanks

---

### Post by btidwell on 2008-04-19
I got this to work by adding xmessage -center -file /path/to/my/startmessage in the System=>Preferences=>Sessions Startup programs. However the message appears after the desktop loads. Would like this to appear before the desktop loads and configure so that the desktop will not load until the user clicks the "OK" button.

---

