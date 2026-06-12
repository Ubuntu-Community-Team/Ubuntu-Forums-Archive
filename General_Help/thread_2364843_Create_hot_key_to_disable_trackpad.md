---
title: "Create hot key to disable trackpad"
date: 2017-06-28
forum: General Help
---

### Post by cc1984 on 2017-06-28
I recently got a new laptop (XPS Dev Ed.) and need a way to quickly turn the trackpad on/off. On my previous laptop I had an fkey that was originally designed to do this but the XPS doesn't have this key. Anyone know how I might be able to create a hot key to turn the trackpad on/off?

Thanks!

---

### Post by ajgreeny on 2017-06-28
If the laptop uses a synaptics touchpad you could possibly do this with a keyboard shortcut for command ```
synclient TouchpadOff=1
```to turn it off and another for ```
synclient TouchpadOff=0
``` to turn it on again.

How you can most easily create a keyboard shortcut will depend on the DE you use, I am not sure how it's done in unity as I seldom use it so have never created one in that.

There may even be a way to toggle on/off with successive key presses of the same shortcut but I'm afraid that is beyond my knowledge.

---

### Post by Tadaen_Sylvermane on 2017-06-28
```
##### variables #####


TOUCHPADID=$(/usr/bin/xinput list | /bin/grep SynPS | /usr/bin/awk '{print $6}' | /usr/bin/awk -F= '{print $2}')
TOUCHPADSTATUS=$(/usr/bin/xinput list-props "$TOUCHPADID" | /bin/grep "Device Enabled" | /usr/bin/awk '{print $4}')


##### begin script #####


if [[ "$TOUCHPADSTATUS" == 1 ]] ; then
	/usr/bin/xinput set-prop "$TOUCHPADID" "Device Enabled" 0
else
	/usr/bin/xinput set-prop "$TOUCHPADID" "Device Enabled" 1
	/usr/bin/synclient TapButton1=1 TapButton2=2 TapButton3=3
fi


##### end script #####

```

I use this script and map to alt m in my i3 window manager. should work just fine. may need to adjust what touchpad to grep for otherwise it should drop right in.

---

