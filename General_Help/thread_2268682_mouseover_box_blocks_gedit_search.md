---
title: "mouseover box blocks gedit search"
date: 2015-03-10
forum: General Help
---

### Post by burninghut on 2015-03-10
I have been having this problem with the search function of gedit, which is really more of a minor annoyance really. After leaving a document open for a while, the mouseover window with the text "String you want to search for" blocks the input box of the search function preventing me from seeing what I'm typing and doesn't disappear until I hide the search function (ctrl + f). Under normal conditions, this window should only appear below the search and disappear when I start typing or move my mouse away from the search. I've attached pictures of what this looks like on my computer. Again, not that big of a deal, especially if you don't make any errors when you type, unlike myself...

So far the only solution I've found is to kill all sessions of gedit and start a new one. All existing sessions of gedit suffer from the bug when it occurs, tabs and windows. If I open a new window or tab in gedit while encountering this problem, it extends to the new instances. I haven't been able to force the bug to happen, but it seems to happen every time I leave a session open long enough (more than 12hrs).

I have no idea how to approach the problem or what parts of gedit/ubuntu control the mouseover pop-up in general. Any advice would be appreciated. Thanks!

I'm running Ubuntu 14.04 and using gedit version 3.10.4

---

### Post by CantankRus on 2015-03-11
I see little positioning bugs like this in compiz.
Next time time it happens see if reloading compiz fixes.
Terminal...
```
setsid unity
```

I find these tooltip windows mostly annoying especially in Opera where unlike firefox
they can't be turned off, so I wrote a script to toggle the opacity of tooltip windows in compiz.

Need to install **compiz-plugins** and **compizconfig-settings-manager** then enable the Opacity,Brightness and Saturation plugin in ccsm.
[ATTACH=CONFIG]260561[/ATTACH]

I created the script as a toggle because occasionally there is info you need to see in tooltips.
Tested in Ubuntu 14.04. Toggles between 0 and 100% opacity.
Save as **tooltips-toggle-trusty.sh** and make executable.
```
#!/bin/bash
#set -x

## Fix For annoying tooltips in chrome and other web browsers
# Script to set up the obs plugin and toggle tooltips on/off.

# Need to install compiz-plugins and then enable the Opacity,Brightness and Saturation plugin.
# First run will configure the obs plugin

# Tested in Ubuntu 14.04

##compiz checks
if apt-cache policy compiz-plugins | grep "Installed: (none)"; then
		notify-send -i error "You need to install compiz-plugins"
			echo "You need to install compiz-plugins"
#		read -p "Press any key to exit this script..."
		exit 0
	else
		obsenabled=$(gsettings get org.compiz.core:/org/compiz/profiles/unity/plugins/core/ active-plugins | grep -c obs)
		if [ $obsenabled = "0" ]; then
				notify-send -i error "You need to Enable the Opacity,Brightness and Saturation plugin in ccsm"
				echo "You need to Enable the obs plugin in ccsm"
#				read -p "Press any key to exit this script..."
				exit 0
			else
				echo "obs plugin enabled...ok"
		fi
fi

## Variable to show tooltip opacity. Opacity of 100% returns "1"
valuetest=$(gsettings get org.compiz.obs:/org/compiz/profiles/unity/plugins/obs/ opacity-values | grep -c 100)
## Variable to check for a tooltip match in the obs plugin
matchtest=$(gsettings get org.compiz.obs:/org/compiz/profiles/unity/plugins/obs/ opacity-matches | grep -c Tooltip)


## check for Tooltip window match entry in obs plugin and add if necessary with an opacity of 0%
if [ $matchtest = "0" ]; then
	gsettings set org.compiz.obs:/org/compiz/profiles/unity/plugins/obs/ opacity-matches "['type=Tooltip']"
	 gsettings set org.compiz.obs:/org/compiz/profiles/unity/plugins/obs/ opacity-values '[0]'
	  echo "tooltip entry added with 0% opacity"
	 notify-send -i window-close "Tooltips" "OFF"
#	read -p "Press any key to exit this script..."
	exit 0
else
	echo "tooltip match exists...toggling tooltip opacity"
fi


## check opacity and toggle between 0 and 100
if [ $valuetest = "1" ]; then

	## set tooltips transparent
	gsettings set org.compiz.obs:/org/compiz/profiles/unity/plugins/obs/ opacity-values '[0]'
	notify-send -i window-close "Tooltips" "OFF"
else	
	## set tooltips opaque
	gsettings set org.compiz.obs:/org/compiz/profiles/unity/plugins/obs/ opacity-values '[100]'
	notify-send -i dialog-apply "Tooltips" "ON"
fi
#read -p "Press any key to exit this script..."
exit 0
```

---

### Post by burninghut on 2015-03-12
Thanks for the feedback! Of course, now that I posted this the bug isn't occurring even though I've had gedit running for 2+ days... It's so insignificant that I'm never paying attention to what I'm doing when it happens. Maybe it has something to do with opening gedit through the terminal, which I haven't been doing a lot of since I posted this. 

Anyway, when the bug happens again (someday) I will try resetting unity, that sounds like it's right.

---

