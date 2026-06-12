---
title: "Xinput settings"
date: 2015-08-31
forum: General Help
---

### Post by yevghenn on 2015-08-31
I have notebook and i use my trackball as mouse.

Trackball cursor is HELL FAST! I cant set settings in Mouse menu for it, because all parameters there already on the left side(minimum speed etc).

So i use command: xinput --set-prop 10 'Device Accel Constant Deceleration' 3 &
Where 10 is my mouse ID. So i can use it with comfort.

But i cant save these settings. After log out or restart or mouse replug i must retype this thing in terminal. Moreover i created .sh file with this command and added file to Startup Applications, but problem is - mouse always change ID everytime i reconnect it.


There is any way to permanently save sensivity-settings for mouse? And i dont want change my touchpad speed, it works fine.

---

### Post by CantankRus on 2015-09-01
Post your ouput from
```
xinput
```

You should be able adapt your script to use your changing
device id at each boot.
eg I can obtain the **[COLOR="#FF0000"]ID[/COLOR]** of my mouse with this.
```
**[COLOR="#006400"]glen@Trusty:~$[/COLOR] xinput**
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Wired Keyboard 600            	id=11	[slave  pointer  (2)]
&#9116;   &#8627; [COLOR="#0000FF"]ZLY ZELOTES GAME MOUSE[/COLOR]                  	id=[COLOR="#FF0000"]**12**[/COLOR]	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Microsoft Wired Keyboard 600            	id=10	[slave  keyboard (3)]

**[COLOR="#006400"]glen@Trusty:~$[/COLOR] xinput --list --id-only '[COLOR="#0000FF"]ZLY ZELOTES GAME MOUSE[/COLOR]'**
**[COLOR="#FF0000"]12[/COLOR]** 
```

Instead of using the changing id, use the name of your device to show the current id.
If your not sure how to do it, post your output from "**xinput**" and the script you're using at startup.

---

