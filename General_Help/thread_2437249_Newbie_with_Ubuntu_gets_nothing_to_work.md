---
title: "Newbie with Ubuntu gets nothing to work"
date: 2020-02-20
forum: General Help
---

### Post by senkora-staraway on 2020-02-20
[COLOR=#000000]So i am new to Ubunu.

Here is my issue. I cant get my graphic card to work. Which is an AMD Ryzen 5 26000X Driver. If i add the HDMI cable it doesnt show anything.
And now my screen randomly freezes. 
Since i couldt get the issue to resolved i tried looking at the erros it gave me

g_queue_pop_head: assertion 'queue != NULL' failed

[/COLOR]
[COLOR=#000000]g_queue_free: assertion 'queue != NULL' failed

[/COLOR][FONT=monospace][COLOR=#000000]bash: /home/maria/.bashrc: regel 118: onverwacht bestandseinde tijdens zoeken naar bijpas[/COLOR]
sende '"'

[/FONT][COLOR=#000000]
[/COLOR][FONT=monospace][COLOR=#000000]bash: /home/maria/.bashrc: regel 119: syntaxfout: onverwacht bestandseinde[/COLOR]

[/FONT]
[COLOR=#000000]Error: Cannot glob /sys/class/rc/rc0/input[0-9]*/event[0-9]*

The last one had to do with some remote controll.
If i try to stop the lircd.socket. Since i so far not use it.  but it, tells me the task stop is not found. And i dont know how to sollute it.

If i open up steam i also get an error

[/COLOR][COLOR=#000000]** (steam:6702): WARNING **: 17:24:45.930: Could not create object for /org/freedesktop/NetworkManager/Devices/1: unknown object type[/COLOR]
[COLOR=#000000]
Sorry for the long post my computer just hates me XD 
any help is very appreciated[/COLOR]

---

### Post by rbmorse on 2020-02-20
The AMD 2600x is your CPU, not a graphics card.  It should work with Ubuntu without any special treatment. 

It would be helpful to know make/model of the graphics adapter (video card)and motherboard in your machine.

---

### Post by TheFu on 2020-02-20
> **rbmorse said:**
> The AMD 2600x is your CPU, not a graphics card.  It should work with Ubuntu without any special treatment. 

It would be helpful to know make/model of the graphics adapter (video card)and motherboard in your machine.

+1 about the Ryzen 5 2600x being a CPU, not a GPU

The easy way to provide an over of the HW, is to install, then run **inxi -Fz**.  Post the output here, wrapped in code tags so it lines up nice.  Please.  Code tags are in the Advanced editor in these forums - (#).

---

### Post by rbmorse on 2020-02-20
Fu sometalks in shorthand.  In case you could use some clarification, the package to install is inxi. Open the terminal application and run the command:  

```
sudo apt install inxi
```

When that's finished, and still using the terminal, run the command: 

```
inxi -Fz
``` 

note the space before the "-" character and the uppercase "F".  Both are important.

---

