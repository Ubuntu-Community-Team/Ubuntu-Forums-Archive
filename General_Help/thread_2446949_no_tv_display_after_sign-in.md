---
title: "no tv display after sign-in"
date: 2020-07-09
forum: General Help
---

### Post by thomathy007 on 2020-07-09
So I'm running Ubuntu 20.04. My TV displays until I sign in, then it just goes blank. I'm using an old NVIDIA Quadro GPU. I'm pretty sure the problem is that the display settings need to be 60 Hz, not 120 Hz, because the TV reports "Display format not supported" and when I connect the TV as a secondary monitor, I can change the display settings from 120 Hz to 60 Hz and then the TV works. But when I connect just the TV, I think the settings revert back to 120 Hz and I don't know how to change them back without a display!

I've tried xrandr from ssh, which reports "can't open display".

I've tried adding an [COLOR=#2E8B57][FONT=Monaco]Option "PreferredMode" "1920x1080_60.00"[/FONT][/COLOR] to xorg.conf, and no dice.

I just need to change the default refresh rate, so it uses that while I'm signed in. The TV only stops working once I sign in!

Update: Some progress made. I've been able to go back and get my old AMD GPU working.
So if I reboot, I normally cannot access display 0 using ssh. So I can sign in using the computer monitor, then reconnect just the TV. Then the display is recognized by xrandr. The defaults are wrong, but I can get the monitor working with the commands below. I have to change the refresh rate twice to get the display working. It doesn't matter if I do 30, then 50 Hz or 50 then 30, I always have to change it twice. 60 Hz doesn't even work and I'm not sure why. So my question is, how can I get this to work on startup? I need this to work before I'm even signed in. Also, the display isn't initially recognized, which is a problem. And there is the issue with the refresh rate. I've tried the Modeline in xorg.conf, but this has only messed things up for me.

```

tombot@Ice-Core-Krystal:~$ DISPLAY=:0 xrandr -s 1920x1080
Can't open display :0
tombot@Ice-Core-Krystal:~$ DISPLAY=:0 xrandr -s 1920x1080
tombot@Ice-Core-Krystal:~$ DISPLAY=:0 xrandr -r 30
tombot@Ice-Core-Krystal:~$ DISPLAY=:0 xrandr -r 50

```

Update 2: I think I need to modify /etc/gdm3/Init/Default, but I want to make sure I do it correctly so I don't mess anything up. Any suggestions?
/etc/gdm3/Init/Default:
```

#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George


PATH="/usr/bin:$PATH"
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


sysresources=/etc/X11/Xresources
# merge in defaults                                                                                     if [ -f "$sysresources" ]; then
    xrdb -merge "$sysresources"
fi


sysmodmap=/etc/X11/Xmodmap


XMODMAP=`gdmwhich xmodmap`
if [ "x$XMODMAP" != "x" ] ; then
  if [ "x$GDM_PARENT_DISPLAY" = "x" ]; then
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
  if [ "x$PROCESSOR" = "xsparc" ]; then
    if $XMODMAP | grep mod4 | grep Alt > /dev/null 2>/dev/null
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
if [ "x$SETXKBMAP" != "x" ] ; then
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
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS" -geometry "$XKBGEOMET>      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS"
      elif [ -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -symbols "$XKBSYMBOLS"
      fi
    fi
  fi
fi


exit 0

```

Update 3: Tried modifying /etc/default/grub with the code below and had no luck. I did "sudo update-grub" afterwards. Changed it back after it didn't work.
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=1920x1080@30"

```


Thanks for the help,
Tom

---

### Post by TheFu on 2020-07-10
I use **lxrandr** for stuff like this. Simple GUI for xrandr.

---

### Post by thomathy007 on 2020-07-11
Hi TheFu, thanks for replying.

I can't use a GUI while I have no display. The only way I can access the display settings directly through the machine, is by plugging in a second monitor. Once I make the changes and unplug the second monitor, the changes are forgotten and it goes back to a blank screen. I can use ssh to manipulate the settings while I'm only connected to tv. I don't get a sign in screen while using the AMD GPU though.

---

