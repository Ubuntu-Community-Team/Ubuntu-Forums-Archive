---
title: "Disable tooltips in google-chrome or opera-dev"
date: 2014-08-21
forum: General Help
---

### Post by CantankRus on 2014-08-21
Anyone know how to disable tooltips which show in the forums using google-chrome and/or opera-developer?

---

### Post by bizhat on 2014-08-21
There is no way you can disable it. It is a feature of vbulletin forum software.

---

### Post by CantankRus on 2014-08-21
> **bizhat said:**
> There is no way you can disable it. It is a feature of vbulletin forum software.
You can disable the popups in firefox in the **about:config** with the setting **browser.chrome.toolbar_tips;false**
I just can't find a similar setting for google-chrome or opera-developer.

---

### Post by bizhat on 2014-08-21
> **CantankRus said:**
> You can disable the popups in firefox in the **about:config** with the setting **browser.chrome.toolbar_tips;false**
I just can't find a similar setting for google-chrome or opera-developer.

Confirmed working on Firefox. I was thinking this is done with java script as some forums i see images too. Never seen such a tooltip for normal web sites.

---

### Post by CantankRus on 2014-08-21
Since I first posted I found a way when using compiz to make the tooltips transparent.
You need to have compiz-plugins installed and using ccsm, enable the **Opacity,Brightness and Saturation** plugin.

I wrote a script to add a window specific setting to the obs plugin and then toggle the tooltips between 0 and 100% opaque.
Works in Ubuntu unity 14.04

tooltips-toggle-trusty.sh
```
#!/bin/bash
#set -x

## Fix For annoying tooltips in chrome and other web browsers
# Script to set up the obs plugin and toggle tooltips on/off.

# May need to install compiz-plugins and then enable the Opacity,Brightness and Saturation plugin.
# First run will configure the obs plugin if required

# Tested in Ubuntu 14.04

## Variable to show tooltip opacity. Opacity of 100% returns "1"
valuetest=$(gsettings get org.compiz.obs:/org/compiz/profiles/unity/plugins/obs/ opacity-values | grep -c 100)
## Variable to check for a tooltip match in the obs plugin
matchtest=$(gsettings get org.compiz.obs:/org/compiz/profiles/unity/plugins/obs/ opacity-matches | grep -c Tooltip)
 

## check for Tooltip window match entry in obs plugin and add if necessary with an opacity of 0%
if [ $matchtest = "0" ]; then
	gsettings set org.compiz.obs:/org/compiz/profiles/unity/plugins/obs/ opacity-matches "['type=Tooltip']"
	gsettings set org.compiz.obs:/org/compiz/profiles/unity/plugins/obs/ opacity-values '[0]'
	echo "tooltip entry added with 0% opacity"
exit 0
else
	echo "tooltip match exists...toggling tooltip opacity"
fi


## check opacity and toggle between 0 and 100
if [ $valuetest = "1" ]; then

	## set tooltips transparent
	gsettings set org.compiz.obs:/org/compiz/profiles/unity/plugins/obs/ opacity-values '[0]'
else	
	## set tooltips opaque
	gsettings set org.compiz.obs:/org/compiz/profiles/unity/plugins/obs/ opacity-values '[100]'

fi
exit 0
```

After the first run of the script the obs plugin in ccsm should look like attached pic.

---

