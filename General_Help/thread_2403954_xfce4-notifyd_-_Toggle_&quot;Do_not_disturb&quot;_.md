---
title: "xfce4-notifyd - Toggle &quot;Do not disturb&quot; via command-line (without GUI)?"
date: 2018-10-18
forum: General Help
---

### Post by tors on 2018-10-18
I wonder if there is a command which will toggle the "Do not disturb" mode of xfce4-notifyd?

Currently I need to go to Settings -> Notifications (or start the GUI with xfce4-notifyd-config) and click the "Do not disturb" toggle button.

---

### Post by Holger_Gehrke on 2018-10-18
```

xfconf-query --channel xfce4-notifyd --property /do-not-disturb --set true # or false to switch do-not-disturb off

```

Holger

---

### Post by #&amp;thj^% on 2018-10-18
With respect to Holger_Gehrke my first run went:
```
me on Thu Oct 18 at 09:00 AM in ~ branch: (HEAD) 
>> xfconf-query --channel xfce4-notifyd --property /do-not-disturb --set true
Property "/do-not-disturb" does not exist on channel "xfce4-notifyd". If a new property should be created, use the --create option.

```

So staying within the OP's request for CLI use my code went:
```
xfconf-query --channel xfce4-notifyd --create --property /do-not-disturb --set true

```
and then the code:
```
xfconf-query --channel xfce4-notifyd --property /do-not-disturb --set true
```
works. :)
Kind Regards

---

### Post by again? on 2018-10-18
Here's a toggle script if you're interested.
```
#!/bin/bash

donotdisturb=$(xfconf-query --channel xfce4-notifyd --property /do-not-disturb)

if [ "$donotdisturb" == "false" ]
	then
		xfconf-query --channel xfce4-notifyd --property /do-not-disturb --set true		
	else
		xfconf-query --channel xfce4-notifyd --property /do-not-disturb --set false
		notify-send -i info "Notifications Enabled"
fi
```

---

### Post by tors on 2018-10-19
Thanks Holger_Gehrke, 1fallen and guber2!

---

