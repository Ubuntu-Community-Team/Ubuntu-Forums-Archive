---
title: "[SOLVED] Script and &amp;quot;export DISPLAY&amp;quot; issues"
date: 2008-06-09
forum: General Help
---

### Post by KingTermite on 2008-06-09
OK....this is a carry over from a thread last night where I was having permission issues with this script, but as this is a completely different issue, I thought I'd start a new thread. I did search for export display threads, but didn't see anything useful enough to solve my problem.

OK....background: This script is taken verbatim (or damn close to) from "Linux Desktop Hacks" book (O'Reilly). The script is called "remindme" and allows you to create reminders to popup on the on-screen display at a predtermined time.

Ex: ***remindme 2:00pm "Call Dr. Suess" ***
would popup a beautiful on screen message (not window or messsage box) with the text I set.

This is the code:

[PHP]#!/bin/bash

#Figure out which display we're using
HOST="$(xrdb -symbols | grep SERVERHOST | cut -d= -f2)"
DISPLAYNUM="$(xrdb -symbols | grep DISPLAY_NUM | cut -d= -f2)"
THISDISPLAY=$HOST:$DISPLAYNUM.0

#check to see if the reminders directory exists (create if not)
if [ ! -e ~/reminders ] ; then
  mkdir ~/reminders
fi

unique=`date +%F-%H-%M-%S`
reminder="reminders/reminder-"$unique

#Now output the reminder script
echo '#!/bin/bash' > ~/$reminder
echo -n 'export DISPLAY=' >> ~/$reminder
echo $THISDISPLAY >> ~/$reminder
echo "echo \"$2 today\" | osd_cat -s 2 -c green -p middle \
-f -adobe-helvetica-bold-r-normal-*-*-240-*-*-p-*-*-* -d 60" >> $reminder

#Make the reminder script executable
chmod +x ~/$reminder

#Schedule it to run
at $1 -f ~/$reminder
[/PHP]

As you can see, what it does is create a reminder script to display the message "on the fly" and sets it to be run with the "at" command.

I finally got it run with no errors, but the message never appeared. So I examined the script it created:

[PHP]#!/bin/bash
export DISPLAY=ktub:0.0
echo "my test message" | osd_cat -s 2 -c green -p middle -f -adobe-helvetica-bold-r-normal-*-*-240-*-*-p-*-*-* -d 60
[/PHP]

It looks correct.

I try to run it manually (no "at" command) and I get an error:
***Error initializing osd: Cannot open display***

I run the main line that displays the message without the DISPlAY setting and it works just fine.

It seems the **export DISPLAY=ktub:0.0** line is the problem. Does anything look wrong with that line?

In case you are interested, here is the output of the **xrdb -symbols** command.

> kt $ xrdb -symbols
-DHOST=ktub
-DSERVERHOST=ktub
-DSRVR_ktub
-DDISPLAY_NUM=0
-DCLIENTHOST=ktub
-DCLNT_ktub
-DVERSION=11
-DREVISION=0
-DVENDOR="The X.Org Foundation"
-DVNDR_The_X_Org_Foundation
-DRELEASE=10400090
-DNUM_SCREENS=1
-DEXT_DAMAGE
-DEXT_Composite
-DEXT_XINERAMA                                                                                     
-DEXT_RANDR
-DEXT_RENDER
-DEXT_XFree86_Bigfont
-DEXT_XFIXES
-DEXT_SECURITY
-DEXT_XAccessControlExtension
-DEXT_XC_APPGROUP
-DEXT_XKEYBOARD
-DEXT_XTEST
-DEXT_XInputExtension
-DEXT_MIT_SHM
-DEXT_XFree86_DRI
-DEXT_RECORD
-DEXT_SGI_GLX
-DEXT_GLX
-DEXT_DOUBLE_BUFFER
-DEXT_X_Resource
-DEXT_XVideo
-DEXT_Extended_Visual_Information
-DEXT_TOG_CUP
-DEXT_DPMS
-DEXT_XFree86_DGA
-DEXT_XFree86_Misc
-DEXT_XFree86_VidModeExtension
-DEXT_XC_MISC
-DEXT_MIT_SCREEN_SAVER
-DEXT_SYNC
-DEXT_BIG_REQUESTS
-DEXT_MIT_SUNDRY_NONSTANDARD
-DEXT_SHAPE
-DSCREEN_NUM=0
-DWIDTH=1440
-DHEIGHT=900
-DX_RESOLUTION=3789
-DY_RESOLUTION=3782
-DPLANES=24
-DBITS_PER_RGB=8
-DCLASS=TrueColor
-DCLASS_TrueColor=35
-DCOLOR
-DCLASS_TrueColor_24=35
-DCLASS_DirectColor_24=43
-DCLASS_TrueColor_32=87


---

### Post by KingTermite on 2008-06-09
P.S. I just took a look at my environment variables to see what DISPLAY was set to by default and it appears to be "nothing" for the host.

> DISPLAY=:0.0

---

### Post by KingTermite on 2008-06-09
OK....nevermind. That was it. I took out the host name and it worked fine.

I just read further on in the book as it was explaining how it worked it mentioned that some versions of osd_cat are cranky and don't want host name in front. Duh! If I'd just read one more paragraph, it would have told me.

---

