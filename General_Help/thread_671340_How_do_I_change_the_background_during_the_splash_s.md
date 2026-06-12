---
title: "How do I change the background during the splash screen?"
date: 2008-01-18
forum: General Help
---

### Post by MR.UNOWEN on 2008-01-18
So as you know when you log in, you get a splash screen or just single color screen (that's what I have) while the computer load your desktop. I know how to change the color of it, but how do you set an image to it? 

Also I want to take it a step further, so how do I get an image or text to fade in and out as well?

> #!/bin/sh
#
# Note that output goes into the .xsession-errors file for easy debugging
#
PATH="/usr/bin:$PATH:/bin:/usr/bin"
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

# Set background color
XSETROOT=`gdmwhich xsetroot`
if [ "x$XSETROOT" != "x" ] ; then

	CHECKBACKCOLOR="OK"
	if [ "x$GDM_GREETER_TYPE" = "xTHEMED" ]; then
		BACKCOLOR=`gdmflexiserver --command="GET_CONFIG greeter/GraphicalThemedColor $DISPLAY"`

		CHECKBACKCOLOR=`echo $BACKCOLOR | sed 's/^\([^ ]*\) .*$/\1/'`
		if [ "x$CHECKBACKCOLOR" = "xOK" ]; then
			BACKCOLOR=`echo $BACKCOLOR | sed 's/^.* \(.*\)$/\1/'`
		else
			BACKCOLOR=""
		fi
	fi

	# If we tried to load the themed backgroundcolor, but failed, then try loading plain color
	if [ "x$CHECKBACKCOLOR" != "xOK" ] || [ "x$GDM_GREETER_TYPE" = "xPLAIN" ]; then

		# Background type can be 0=None, 1=Image & Color, 2=Color, or 3=Image 
		BACKTYPE=`gdmflexiserver --command="GET_CONFIG greeter/BackgroundType $DISPLAY"`

		# Skip if background type does not include a color
		if [ "x$BACKTYPE" = "xOK 1" ] || [ "x$BACKTYPE" = "xOK 2" ]; then
			BACKCOLOR=`gdmflexiserver --command="GET_CONFIG greeter/BackgroundColor $DISPLAY"`

			CHECKBACKCOLOR=`echo $BACKCOLOR | sed 's/^\([^ ]*\) .*$/\1/'`
			if [ "x$CHECKBACKCOLOR" = "xOK" ]; then
				BACKCOLOR=`echo $BACKCOLOR | sed 's/^.* \(.*\)$/\1/'`
			else
				BACKCOLOR=""
			fi
		fi
	fi

	# Default value
 	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="#78b0ea"
 	fi

	"$XSETROOT" -cursor_name left_ptr -solid "$BACKCOLOR"
fi

exit 0

---

### Post by jeffus_il on 2008-01-18
Here is the splash screen stuff:
[http://ubuntuforums.org/showthread.php?t=11478](http://ubuntuforums.org/showthread.php?t=11478)

---

### Post by MR.UNOWEN on 2008-01-21
Is there a way I can do it through the provided file? The issue is the splash screen only shows for a few seconds and the remainder of the loading is a blue screen, So I want to do it through the provided file. Or even better...  can I have it load and terminate a jar file from the provided file?

---

### Post by MR.UNOWEN on 2008-01-22
By the way what kind of coding is this:

> #!/bin/sh
#
# Note that output goes into the .xsession-errors file for easy debugging
#
PATH="/usr/bin:$PATH:/bin:/usr/bin"
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

# Set background color
XSETROOT=`gdmwhich xsetroot`
if [ "x$XSETROOT" != "x" ] ; then

CHECKBACKCOLOR="OK"
if [ "x$GDM_GREETER_TYPE" = "xTHEMED" ]; then
BACKCOLOR=`gdmflexiserver --command="GET_CONFIG greeter/GraphicalThemedColor $DISPLAY"`

CHECKBACKCOLOR=`echo $BACKCOLOR | sed 's/^\([^ ]*\) .*$/\1/'`
if [ "x$CHECKBACKCOLOR" = "xOK" ]; then
BACKCOLOR=`echo $BACKCOLOR | sed 's/^.* \(.*\)$/\1/'`
else
BACKCOLOR=""
fi
fi

# If we tried to load the themed backgroundcolor, but failed, then try loading plain color
if [ "x$CHECKBACKCOLOR" != "xOK" ] || [ "x$GDM_GREETER_TYPE" = "xPLAIN" ]; then

# Background type can be 0=None, 1=Image & Color, 2=Color, or 3=Image
BACKTYPE=`gdmflexiserver --command="GET_CONFIG greeter/BackgroundType $DISPLAY"`

# Skip if background type does not include a color
if [ "x$BACKTYPE" = "xOK 1" ] || [ "x$BACKTYPE" = "xOK 2" ]; then
BACKCOLOR=`gdmflexiserver --command="GET_CONFIG greeter/BackgroundColor $DISPLAY"`

CHECKBACKCOLOR=`echo $BACKCOLOR | sed 's/^\([^ ]*\) .*$/\1/'`
if [ "x$CHECKBACKCOLOR" = "xOK" ]; then
BACKCOLOR=`echo $BACKCOLOR | sed 's/^.* \(.*\)$/\1/'`
else
BACKCOLOR=""
fi
fi
fi

# Default value
if [ "x$BACKCOLOR" = "x" ]; then
BACKCOLOR="#78b0ea"
fi

"$XSETROOT" -cursor_name left_ptr -solid "$BACKCOLOR"
fi

exit 0

---

### Post by MR.UNOWEN on 2008-01-25
Anyone?

---

### Post by tad1073 on 2008-01-25
Look in the repositories for Gnome Slash Screen.

---

### Post by MR.UNOWEN on 2008-01-25
> **tad1073 said:**
> Look in the repositories for Gnome Slash Screen.

Well I managed to get a splash screen to show from that other link. The issue is that it doesn't show up for long. 85% is a blue screen (as I've modified the code to show blue) and the other 15% is the image I selected. 

My question now, is how to I modify the code above such that an image will be displayed instead of just a single color.

---

