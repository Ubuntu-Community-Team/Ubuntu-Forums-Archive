---
title: "Master Volume"
date: 2005-10-15
forum: General Help
---

### Post by Dgurion on 2005-10-15
Shouldnt the master volume control also control the volume of the headphones if you have the "Headphone Jack Sense" enabled. because I have built in buttons on my laptop and they only control the "master" sound. So if I have headphones plugged in I have to open the sound-control and change it in there.. Not really a problem but It would be nice to have it control the headphones volume when you have headphones plugged in and you have the headphones jack sense enabled...

---

### Post by plutoprime on 2005-10-15
I hope they fix this problem too :(

---

### Post by JazzCrazed on 2005-10-16
My problem on my laptop is that the keyboard volume controls the master volume, but the master volume seems to bear no effect on the speaker volume!

Instead, it's controlled via the sliders for both "headphone" and "PCM" in the volume controls.

:confused:

---

### Post by moopere on 2005-10-16
[QUOTE=JazzCrazed]My problem on my laptop is that the keyboard volume controls the master volume, but the master volume seems to bear no effect on the speaker volume!

Instead, it's controlled via the sliders for both "headphone" and "PCM" in the volume controls.

:confused:[/QUOTE]

Yeah, its a bit 'wrong' isn't it :)  You'll also notice that with the new fabulous laptop multimedia key recognition thing we've got for Breezy that it appears to be hardcoded to manipulate the master volume only.

So, if you think you're pretty smart, like I did, and have changed your panel volume control to 'pcm' instead of master (in order to get headphone & speaker control) you can't use your laptops multimedia keys !!! (Arrgghh!).

:)

Craig

---

### Post by tedddee on 2005-11-27
Having the same problem here :(

---

### Post by djlosch on 2005-11-27
[volmute](http://www.djlosch.com/post_retrieve.php?pid=59#pcm_volume_link) Just Works (tm!)

---

### Post by tedddee on 2005-11-29
ok that link is great, i got this volmute working in a terminal

[IMG]http://s87055070.onlinehome.us/ted/photo/Screenshot-ted@EVA02:%20~.png[/IMG]

however, i cant seem to get the commands to pass through my keyboard buttons.  i'm pretty sure i've set it up correctly :(

these are the defeault bindings that work (bring up on-screen volume thingy) but control Master volume, and thus useless for me

[IMG]http://s87055070.onlinehome.us/ted/photo/Screenshot-Keyboard%20Shortcuts.png[/IMG]

so i tried to create my own, but they dont want to work

[IMG]http://s87055070.onlinehome.us/ted/photo/Screenshot-Configuration%20Editor%20-%20global_keybindings.png[/IMG]

[IMG]http://s87055070.onlinehome.us/ted/photo/Screenshot-Configuration%20Editor%20-%20keybinding_commands.png[/IMG]

the 3ddesk hotkey works fine, so im not quite sure why these dont :confused:

---

### Post by Chris Tucker on 2005-11-29
i managed to get mine to work, had the same prob, so i did a search, and this worked exactly perfect:
[http://ubuntuforums.org/showthread.php?t=27039&highlight=metacity+key+codes](http://ubuntuforums.org/showthread.php?t=27039&highlight=metacity+key+codes)
only thing is you dont see the volume dialog when you use them.. next prob to fix later this winter :D

---

### Post by tedddee on 2005-11-30
Where can I find "/usr/lib/X11/XKeysymDB" from that How To?  Don't have that file on my Breezy.

edit: never mind found it in /usr/share/X11, great link got the hotkeys working with volmute to control PCM :)

---

### Post by Chris Tucker on 2005-12-01
oops, forgot to mention that, yea its /usr/share/X11  any nice finding app will help you as you probably found.

---

### Post by .t. on 2005-12-21
For those KDE users out there: [http://www.unicom.com/chrome/a/001028.html](http://www.unicom.com/chrome/a/001028.html)
 is a good link!

---

### Post by StianH on 2005-12-22
Any suggestions on how to change the function of my volume up/down/mute keys from "Heaphones" to "PCM" volume?

---

### Post by djlosch on 2006-12-08
> **StianH said:**
> Any suggestions on how to change the function of my volume up/down/mute keys from "Heaphones" to "PCM" volume?
use the [volmute](http://www.djlosch.com/post_retrieve.php?pid=59#pcm_volume_link) script (i don't claim credit for it, i got it off FGO).  then use one of the many howtos for assigning multimedia keys to scripts.  depending on whether you use kde or gnome, global key assignments are different.

---

### Post by ingomueller.net on 2007-01-11
Hi!

I had a similar problem one month ago and have spent a lot of time in its solution. As I stumbled upon this post, probably others will, so I'll post the link to a howto I wrote:

[http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume](http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume)

I hope this helps someone...

Ingo

---

