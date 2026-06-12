---
title: "volume randomly increases on it's own"
date: 2013-12-03
forum: General Help
---

### Post by rad_sci_guy on 2013-12-03
I've been having this problem for the past 2 weeks in which the volume will randomly increase to maxium all on its own and the volume notification will keep flashing unit I press the volume buttons on my keyboard.  It looks similar as if you are holding down to the volume up button on the keyboard.  I have tried several different keyboards and the problem is still happening.  I don't know how to stop this.  Does anyone else have this issue and does anyone know how to fix it?  I'm using Ubuntu 13.10.  Didn't have this problem on previous releases.

thanks

---

### Post by PaulBx on 2013-12-03
Do you have a touchpad? I have one and all sorts of weird things would happen even if I was not touching it, due to extreme sensitivity. Since I normally use a mouse anyway I put up a little icon to disable the touchpad. Here is what I put in my Desktop directory:

```

[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Toggle the touchpad
Name[en_US]=Toggle the touchpad
Exec=/home/paul/touch_toggle.sh
Comment[en_US]=
Terminal=false

```

Here is the script:

```

#
# tp_toggle
#
# Toggle the touchpad on/off.


# Get the id number of the touchpad.
tp_id=`xinput list | grep -i touchpad | awk '{ print $6 }' | sed 's/id=//'`


# Find out whether the touchpad is enabled or not.
tp_enabled=`xinput list-props $tp_id | grep Device\ Enabled | awk '{ print $4 }'`


if [ $tp_enabled = 0 ]
then
  # The touchpad is currently disabled, so turn it on.
  xinput set-prop $tp_id "Device Enabled" 1
  echo "Touchpad now on."
elif [ $tp_enabled = 1 ]
then
  # The touchpad is currently enabled, so turn it off.
  xinput set-prop $tp_id "Device Enabled" 0
  echo "Touchpad now off."
else
  echo "tp_toggle: Could not get touchpad status from xinput."
  exit 1
fi

```

I didn't code it myself, just found it somewhere and it worked for me.

---

### Post by rad_sci_guy on 2013-12-04
Thanks for your reply but I don't have a touchpad.  Just a wireless mouse and wired keyboard.   It just started happening.  I've also got a dual boot with Kubuntu 13.10 and the same thing is happening there as well althought it doesn't seem to be as frequent.

---

