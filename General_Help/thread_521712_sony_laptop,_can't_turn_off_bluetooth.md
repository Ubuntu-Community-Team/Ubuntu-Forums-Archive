---
title: "sony laptop, can't turn off bluetooth"
date: 2007-08-09
forum: General Help
---

### Post by vladuz976 on 2007-08-09
Hi,

have feisty on a sony vaio vgn-c71b,
everything works great except for the bluetooth. I cannot turn it off, or I don't know how to. I don't see anything in the menus for it. my cell phone finds my laptop as a device but I cannot connect to it.

Thank you very much,

Eric Dan

---

### Post by ruibernardo on 2007-08-09
> **vladuz976 said:**
> Hi,

have feisty on a sony vaio vgn-c71b,
everything works great except for the bluetooth. I cannot turn it off


Hi vladuz,

did you try this?

```
sudo /etc/init.d/bluetooth stop
```

If you really don't want bluetooth to work anymore, edit the file /etc/default/bluetooth:

```
sudo nano /etc/default/bluetooth
```

and change the BLUETOOTH_ENABLED option to 0:

```
BLUETOOTH_ENABLED=0
```

Cheers.

---

### Post by vladuz976 on 2007-08-09
thanks for the tip. 
I just tried that and the terminal responds with stopped [ok]
but the bluetooth light is still on and i can still detect the laptop with my phone.
i set the /etc file to ---> 0
restarted, but still on.

---

### Post by ruibernardo on 2007-08-09
Do you have installed kdebluetooth, or anything else that uses and manages bluetooth too?

You must have something that isn't controled by the default Ubuntu service.

---

### Post by vladuz976 on 2007-08-09
just default ubuntu install with gnome.
no kde.

---

### Post by ruibernardo on 2007-08-09
Can you open the file /etc/default/bluetooth and check if HIDD_ENABLED is zero?

---

### Post by vladuz976 on 2007-08-09
yes, i checked. it's set to 0.

---

### Post by ruibernardo on 2007-08-09
Other options it this file that should be zero:

DUND_ENABLED
PAND_ENABLED

---

### Post by vladuz976 on 2007-08-09
those are set to 0 as well.

---

### Post by ruibernardo on 2007-08-09
Do you have anything in Gnome Sessions that sets anything related to Bluetooth? To make it discoverable?

---

### Post by vladuz976 on 2007-08-09
Not that I know.
can you give me a hint what to look for?

---

### Post by ruibernardo on 2007-08-09
Something like:

```
 dbus-send --system --dest=org.bluez /org/bluez/hci0 org.bluez.Adapter.SetMode string:discoverable
```

It's used to make bluetooth visible to other devices.

Maybe you changed some settings in gconf-editor to make some tweak to bluetooth in Gnome. Search there.

---

### Post by vladuz976 on 2007-08-09
actually this issue has been going on since I bought and installed ubuntu.
from the first boot til now. no change.

---

### Post by ruibernardo on 2007-08-09
This is very strange.

Just to confirm that bluetooth IS really working. Delete the computer bluetooth device in your phone and remove it from trusted devices too. Then, try scanning again.

---

### Post by vladuz976 on 2007-08-09
yeah just did that and searched again for devices and it found my laptop again.but I can't connect to it.

---

### Post by ruibernardo on 2007-08-09
Well, I'm out of ideas. :( 

If you really don't want to your Vaio to be "visible" and you don't use Bluetooth, I would suggest you to disable Bluetooth in the BIOS settings of your computer.

Maybe somebody else that have a Sony Vaio can help you.

Cheers.

---

### Post by wieman01 on 2007-08-11
There you go...

You need to install a tool called "spictrl". 
> sudo apt-get install spicctrl
> sudo modprobe sonypi
> gksudo gedit /etc/modules
Now add this at the bottom of the file:
> [COLOR="Red"]sonypi[/COLOR]
Now turn off the Bluetooth device:
> sudo spicctrl -l 0
If you need a startup script for turning it off at boot, let me know. I set on up for you.

---

### Post by vladuz976 on 2007-08-11
thanks a lot for the help. I followed every step. the terminal didn't return any error messages, but bluetooth is still on!

by the way, isn't spicctrl a package to control the battery and the lcd backlight?

---

### Post by wieman01 on 2007-08-11
> **vladuz976 said:**
> thanks a lot for the help. I followed every step. the terminal didn't return any error messages, but bluetooth is still on!

by the way, isn't spicctrl a package to control the battery and the lcd backlight?
Have you restarted the PC? Forgot to mention it... Try to turn it off again after a restart.

---

### Post by vladuz976 on 2007-08-11
Ok, I restarted, then I turned it off again in command line, but it's still on. I just can't turn it off.

---

