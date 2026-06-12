---
title: "Browser remote control -- TV-like flipping online video channels"
date: 2013-04-06
forum: General Help
---

### Post by Rebelli0us on 2013-04-06
Donating my script-let. We use this for watching evening news online and youtube videos while sitting on the living room couch (or in bed). 

Because of time difference some channels can be offline, or just boring, so this script is a convenient way of flipping through our favorite broadcasts without a keyboard.


```
#!/bin/bash
# Flips Firefox URLs just like TV channels.
# Operated by wireless USB remote control or through command line.
# Script must be called with command line parameter + or -
# Flips URL in current Firefox tab to the next/previous (+/-) channel from
# a list of pre-selected URLs (links) stored in URL_INDEX_DIRECTORY.
#
# To create a list of favorite channels, drag links from Firefox&#8217;s URL bar into the
# URL_INDEX_DIRECTORY. Channels will be presented alphabetically. 
# For added convenience you can create a link to URL_INDEX_DIRECTORY on
# your desktop and name it &#8220;Firefox Channels&#8221; or whatever you prefer. This way
# you can drag browser URLs there instead of opening your ~/Documents/... folder.
# To remove channels simply open your channel folder and delete them.
#
# To activate the remote control, in Linux Preferences create two new Keyboard Shortcuts:
#
# Name: Channel UP
# Command: /home/<User Name>/Documents/firefox-control.sh -
#
# Name: Channel DOWN
# Command: /home/<User Name>/Documents/firefox-control.sh +
#
# Click on &#8220;shortcut&#8221; and press an available key on the remote control.
# Assign any 2 adjacent macro keys, or the multimedia next/previous keys. 
# Should work with any remote. I tested with &#8220;Wireless USB PC Remote Control Mouse&#8221;
# available on Amazon for $7, ASIN: B001M56DI0, Item model number: SNX_PC-RC1
#
# You may locate this script anywhere you like, but make it executable.
# You may also modify the paths defined below to suit your preferences.
# Please install &#8220;xdotool&#8221;, available through Synaptic Package Manager.


CURRENT_CHANNEL_FILE="/home/$USER/Documents/firefox-control-channel"
 URL_INDEX_DIRECTORY="/home/$USER/Documents/firefox-control-channel-index"

if [ ! -d "$URL_INDEX_DIRECTORY" ]; then
	mkdir "$URL_INDEX_DIRECTORY"
	echo -e [Desktop Entry]\\nName=Link to Google\\nType=Link\\nURL=http://www.google.com/ > "$URL_INDEX_DIRECTORY"/Google.desktop
fi

# Change current channel up/down based on command line argument -/+
CHANNEL_NUMBER=$(($(sed -n '1p' $CURRENT_CHANNEL_FILE)${1}1))

# Was at channel 0, cycle down to the end of the URL index.
if [ "$CHANNEL_NUMBER" = -1 ]; then
	# Get zero-based file/channel count
	CHANNEL_NUMBER=$(($(ls -1 "$URL_INDEX_DIRECTORY"/*.desktop | wc -l)-1))	
fi

# Get URL for current channel
OIFS=$IFS
IFS=$'\n' 
array=($(ls -A "$URL_INDEX_DIRECTORY"/*.desktop))
IFS=$OIFS
CHANNEL_URL="${array[$CHANNEL_NUMBER]}"

# Reached the end of the URL index, cycle back up to the top.
if [ "$CHANNEL_URL" = "" ]; then
	CHANNEL_NUMBER=0
	CHANNEL_URL="${array[0]}"
fi

echo Channel $CHANNEL_NUMBER \> "$CHANNEL_URL"

# Save current channel #
echo $CHANNEL_NUMBER > $CURRENT_CHANNEL_FILE

xdotool windowactivate $(xdotool search --name "Mozilla Firefox")

# Click on Firefox's URL bar to take focus away from Adobe Flash.
# This is ugly code, but Adobe Flash steals keyboard focus thus preventing
# Firefox from responding to keyboard commands, such as the following Ctrl+F4.
# Clicking on a different tab (and other locations) takes focus away from Flash
# allowing the browser to operate normally.
# If mouse click in this location causes problem, coordinates can be modified:
# Run &#8220;xdotool getmouselocation&#8221; to obtain a more appropriate screen location.
xdotool mousemove 500 50 click 1

# Close current tab in Firefox.
# This is to prevent many tabs playing flash video simultaneously.
# Firefox will not close the last tab, instead produces an error
# message and closes. So two tabs or more works better.
xdotool key ctrl+F4

# Open the URL
#xdg-open "$CHANNEL_URL"
firefox "$CHANNEL_URL"

#/*

```

---

### Post by Rebelli0us on 2013-04-16
An update: The following 2 xdotool lines can be deleted or commented out:

xdotool mousemove 500 50 click 1
xdotool key ctrl+F4

**IF** Firefox option “browser.link.open_newwindow” is set to 1, will open links in the current tab.
This option is not available through Firefox Tab options, so use “about:config”.

---

### Post by Rebelli0us on 2013-04-16
And no remote control would be complete without a **sleep-timer**: 



```
#!/bin/bash

# This setting is for Linux Mint MATE, for Ubuntu use “gconftool-2” instead of “mateconftool-2”, and
# MATECONF_KEY="/apps/gnome-power-manager/timeout/sleep_computer_ac"
# e.g. “gconftool-2 --type int --set /apps/gnome-power-manager/timeout/sleep_computer_ac _____”


MATECONF_KEY="/apps/mate-power-manager/timeout/sleep_computer_ac"

HOURS=$(zenity --list --title "Sleep Timer" \
--text="<span font-family=\"sans\" font-weight=\"900\" font-size=\"xx-large\">\
Current setting: $(($(mateconftool-2 --get $MATECONF_KEY)/3600)) hrs</span>" \
--width=300 --height=350 --column "Hours" 0 1 2 3 4 5 6)

echo \"$HOURS\"

if [ "$HOURS" != "" ]; then
	mateconftool-2 --type=int --set $MATECONF_KEY $(($HOURS*3600))
fi

exit



```

---

