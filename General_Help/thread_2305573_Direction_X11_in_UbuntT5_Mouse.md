---
title: "Direction X11 in UbuntT5 Mouse"
date: 2015-12-07
forum: General Help
---

### Post by tristantonks-b on 2015-12-07
Hi Guys,
Hope someone can help - I've searched the forums a dozen times and I cannot find anything that works to get my Mad Catz Mad Catz R.A.T.5 Mouse working in Ubuntu 15
I'm sure how to check but it's my understanding that x11 is no longer used?
Can anyone point me in the right direction please.

---

### Post by grahammechanical on 2015-12-07
> it's my understanding that x11 is no longer used?

Incorrect understanding. Ubuntu is still using X in 15.10 and it will still be using X in 16.04 which will be supported for 5 years. In the future X will be replaced by Mir. In fact Mir is used in the Ubuntu phone OS. And there is work being done to converge the code of the phone OS with the code of the desktop OS so that there is one code base for all Ubuntu versions. But the convergence has not yet taken place. And I have not heard anything to indicate that 16.04 will be running on Mir at all during its life span. There may be a version of Ubuntu running on Mir with the 16.10 release. May be. Cannot say more than that.

Regards.

---

### Post by tristantonks-b on 2015-12-07
Thanks Grahammechanical....

So I've checked the following locations;
etc/X11/..... not exist - I created; /X11/xorg.conf but nothing.. (Deleting)
Then;
usr/share/X11/... nothing -

---

### Post by QDR06VV9 on 2015-12-07
> **tristantonks-b said:**
> Hi Guys,
Hope someone can help - I've searched the forums a dozen times and I cannot find anything that works to get my Mad Catz Mad Catz R.A.T.5 Mouse working in Ubuntu 15
I'm sure how to check but it's my understanding that x11 is no longer used?
Can anyone point me in the right direction please.
See if this is of any help
[https://wiki.archlinux.org/index.php/Mad_Catz_Mouse](https://wiki.archlinux.org/index.php/Mad_Catz_Mouse)
I got a R.A.T.3 working with this method for a friend.
Be sure to note here that a file for Xorg must be created.
> [FONT=sans-serif]The issues are caused by an interaction between R.A.T Mode button and the X Server. To restore proper function, the 'Mode' button must be disabled, as follows:[/FONT][FONT=sans-serif]With root privileges, create and edit the file **/etc/X11/xorg.conf.d/50-vmmouse.conf** (see [xorg]("https://wiki.archlinux.org/index.php/Xorg")).[/FONT]
[FONT=sans-serif]Add the following content :[/FONT]
Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "evdev"
    Option         "Name" "Saitek Cyborg R.A.T.3 Mouse"
    Option         "Vendor" "06a3"
    Option         "Product" "0ccc"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/event4"
    Option         "Emulate3Buttons" "no"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 4 5 6 7 0 0 0 0 0 0 0"
    Option         "Resolution" "3200"
EndSection 
[FONT=sans-serif]After restarting your X server, the mouse should be fully functional, including the two lateral buttons. If not, or if you need more informations about configuring gaming mice, see [/FONT][All Mouse Buttons Working]("https://wiki.archlinux.org/index.php/All_Mouse_Buttons_Working")[FONT=sans-serif].[/FONT]
You may or may not have to change
```
"Saitek Cyborg R.A.T.3 Mouse"
```
To your specific mouse name.
Regards

---

### Post by coffeecat on 2015-12-07
*Thread moved to **General Help**.*

---

