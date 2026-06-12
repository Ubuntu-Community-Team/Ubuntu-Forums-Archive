---
title: "Working Script that Emulate Quake Xterm using wmctrl only"
date: 2012-11-01
forum: General Help
---

### Post by honeybear on 2012-11-01
Hello, 

Simply add this command to your openbox config : .config/openbox/rc.xml 

```

    <keybind key="W-F12">
      <action name="Execute">
        <execute>  sh ~/quake-xterm.sh  </execute>
      </action>
    </keybind>

```



```



#!/bin/sh
# quake_rxvt: emulates quake terminal functionality
# designed for use with openbox and wmctrl


# make sure wmctrl exists
wmctrlpath="$( which wmctrl &>/dev/null )"
if ! [ -x "$wmctrlpath" ] ; then
  echo Error: required dependency wmctrl not found. >&2
  exit 1
fi

QUAKEID=` wmctrl -l   | grep "screen$" | awk ' { print $1 } ' `
active_window_id="$QUAKEID"
WIDTHMAX="$((`xrandr  | head -n 1 | cut -d"," -f2-2 | awk '  { print $2 }'` -2  ))"
HEIGHTMAX="$((`xrandr  | head -n 1 | cut -d"," -f2-2 | awk '  { print $4 }'` -55  ))"
HEIGHTZENITY="650"
if [ $HEIGHTZENITY -gt $HEIGHTMAX ] ; then 
  HEIGHTZENITY="$HEIGHTMAX"
fi
HEIGHTMAXR=$(( $HEIGHTMAX / 10))
WIDTHMAXR=$(( $WIDTHMAX / 6 ))

if [ "$QUAKEID" != "" ] ; then 
  WMICO=`xprop -id "$QUAKEID" | grep  -A3  "WM_STATE(WM_STATE):" | grep state  | grep Iconic`
  WMNOR=`xprop -id "$QUAKEID" | grep  -A3  "WM_STATE(WM_STATE):" | grep state  | grep Normal`
  echo "State: $WMICO $WMNOR"

  if [ "$WMICO" != "" ] ; then 
    wmctrl -i -a "$active_window_id" 
  elif [ "$WMNOR" != "" ] ; then 
    wmctrl -i -r "$active_window_id" -b add,hidden 
  fi
else
  SESSIONQUAKESCREEN=`screen -ls     | grep session.quake | awk ' { print $1 } ' | awk -F "." ' { print $1 } '  | tail -n 1`
  if [ "$SESSIONQUAKESCREEN" != "" ] ; then 
    # notify-send "SE $SESSIONQUAKESCREEN"
    xterm -bg black -fg green  -g  $HEIGHTMAXRx$WIDTHMAXR+0+0   -e screen -D -r "$SESSIONQUAKESCREEN"
  else
    notify-send "New Quake Screen"
    xterm -bg black -fg green    -g  $HEIGHTMAXRx$WIDTHMAXR+0+0  -e screen -S session.quake  
  fi
fi


```

---

### Post by honeybear on 2012-12-16
Hi Guys, 

this is a much better version of this quake xterm !!

If you try this script, do not hesitate to post / let me know.

Enjoy!

---

### Post by honeybear on 2012-12-16
Simply add this command to your openbox config : .config/openbox/rc.xml 

```

    <keybind key="W-F12">
      <action name="Execute">
        <execute>  bash ~/quake-xterm.sh   </execute>
      </action>
    </keybind>

```

---

