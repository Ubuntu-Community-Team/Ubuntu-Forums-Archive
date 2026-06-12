---
title: "Num Lock and System Beep--Gutsy"
date: 2007-07-30
forum: General Help
---

### Post by LuxVoodoo on 2007-07-30
Just upgraded to Gutsy a couple of days ago and so far things have run pretty smoothly, all things considered.  However, I've had numlockx installed on my system for a while now so I didn't have to press it every time I logged in.  This stopped working when I went to Gutsy.  I retraced my steps and followed this guide to reinstall it:

[http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_135.html]("http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_135.html")

However, when it gets to the > sudo gedit /etc/X11/gdm/Init/Default step, that file is now blank.  No "Exit0".   Nothing.  And I'm not sure what needs to be put there.  Any ideas?

The only reason this is bugging me is because without the Num Lock activated, my system gives off a system beep, even though I have system beep disabled.

Thanks in advance!  :-)

---

### Post by nitro_n2o on 2007-07-30
Here my /etc/gdm/Init/Default file it's from 7.04 haven't edited anything 
```
#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

PATH=/usr/X11R6/bin:$PATH
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}


sysmodmap=/etc/X11/Xmodmap

XMODMAP=`gdmwhich xmodmap`
if [ x$XMODMAP != x ] ; then
  if [ x$GDM_PARENT_DISPLAY = x ]; then
    if [ -f $sysmodmap ]; then
      $XMODMAP $sysmodmap
    fi
  else
    ( DISPLAY=$GDM_PARENT_DISPLAY XAUTHORITY=$GDM_PARENT_XAUTHORITY $XMODMAP -pke ) | $XMODMAP -
  fi

  #
  # Switch Sun's Alt and Meta mod mappings
  #

  UNAME=`gdmwhich uname`
  PROCESSOR=`$UNAME -p`
  if [ x$PROCESSOR = xsparc ]; then
    if $XMODMAP | /usr/bin/grep mod4 | /usr/bin/grep Alt > /dev/null 2>/dev/null
    then
      $XMODMAP -e "clear Mod1" \
               -e "clear Mod4" \
               -e "add Mod1 = Alt_L" \
               -e "add Mod1 = Alt_R" \
               -e "add Mod4 = Meta_L" \
               -e "add Mod4 = Meta_R"
    fi
  fi
fi

SETXKBMAP=`gdmwhich setxkbmap`
if [ x$SETXKBMAP != x ] ; then
  # FIXME: is this all right?  Is this completely on crack?
  # What this does is move the xkb configuration from the GDM_PARENT_DISPLAY
  # FIXME: This should be done in code.  Or there must be an easier way ...
  if [ -n "$GDM_PARENT_DISPLAY" ]; then
    XKBSETUP=`( DISPLAY=$GDM_PARENT_DISPLAY XAUTHORITY=$GDM_PARENT_XAUTHORITY $SETXKBMAP -v )`
    if [ -n "$XKBSETUP" ]; then
      XKBKEYMAP=`echo "$XKBSETUP" | grep '^keymap' | awk '{ print $2 }'`
      XKBTYPES=`echo "$XKBSETUP" | grep '^types' | awk '{ print $2 }'`
      XKBCOMPAT=`echo "$XKBSETUP" | grep '^compat' | awk '{ print $2 }'`
      XKBSYMBOLS=`echo "$XKBSETUP" | grep '^symbols' | awk '{ print $2 }'`
      XKBGEOMETRY=`echo "$XKBSETUP" | grep '^geometry' | awk '{ print $2 }'`
      if [ -n "$XKBKEYMAP" ]; then
        $SETXKBMAP -keymap "$XKBKEYMAP"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" -a -n "$XKBGEOMETRY" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS" -geometry "$XKBGEOMETRY"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS"
      elif [ -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -symbols "$XKBSYMBOLS"
      fi
    fi
  fi
fi

exit 0
```
Did u try to turn the NumLock on from the bios settings? that should work, i'm not sure about gutsy
good luck

---

### Post by NilsE on 2007-07-30
In Gutsy it is in a different place

/etc/gdm/Init/Default

---

### Post by LuxVoodoo on 2007-07-30
> **NilsE said:**
> In Gutsy it is in a different place

/etc/gdm/Init/Default

This did the trick, so thank you very much!  I now don't have to toggle Num Lock at login.  However, I'm still getting a system beep at the login screen even though system beep is disabled in sounds.  Any ideas on that?  Ahhhhh...I love putting my Ubuntu back together after a dist upgrade.  :-)

---

### Post by NilsE on 2007-07-30
> **LuxVoodoo said:**
> This did the trick, so thank you very much!  I now don't have to toggle Num Lock at login.  However, I'm still getting a system beep at the login screen even though system beep is disabled in sounds.  Any ideas on that?  Ahhhhh...I love putting my Ubuntu back together after a dist upgrade.  :-)

Check in 2 places to see if a tone is set on.

1 - Login Menu sounds on Login Window on System/Administration (may need to activate in Main Menu)

2 - Sound preferences on System/Preferences menu

You may just be getting a regular sound if you have disabled system beeps

If you are still getting the PC beeps try (if you have done it a different way) 

gksudo gedit /etc/rc.local

and add the following just above the exit 0

modprobe -r pcspkr

---

### Post by LuxVoodoo on 2007-07-30
> **NilsE said:**
> Check in 2 places to see if a tone is set on.

1 - Login Menu sounds on Login Window on System/Administration (may need to activate in Main Menu)

This turned out to be the culprit, and you would've thought I'd figure it out since I've been with Ubuntu since Dapper.  Turns out a login sound was checked, but the preview sound box was grayed out because no sound had been selected.  So the system must've been beeping by default or something. It's all good now and I really thank you for your help.  I guess sometimes the fix is right there in front of you.  :-)

Thanks again.

---

### Post by NilsE on 2007-07-30
Glad it worked out.  I hate that system beep also.

---

### Post by AlexThomson_NZ on 2007-07-30
Yeah the whole modprobe -r thing is usually the first thing I do after an install.  I wonder if it's worth proposing as standard behaviour in Gusty?

---

### Post by NilsE on 2007-07-30
> **AlexThomson_NZ said:**
> Yeah the whole modprobe -r thing is usually the first thing I do after an install.  I wonder if it's worth proposing as standard behaviour in Gusty?
In Gutsy the option to turn off the system beep in the sound preferences actually works.  I removed the modprobe and it is fine so I guess it is fixed from a properties perspective.

---

### Post by AlexThomson_NZ on 2007-07-30
Cool thanks for the info NilsE!

---

