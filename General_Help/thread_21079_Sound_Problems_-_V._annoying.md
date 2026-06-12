---
title: "Sound Problems - V. annoying"
date: 2005-03-20
forum: General Help
---

### Post by seasidebaz on 2005-03-20
I'm having a stupid sound problem.
Alerts and stuff like that play through the speakers normally, but when I load up amaroK or xmms nothing will play, and I get an error saying there is no sound system. I recently did a dist-upgrade from warty to hoary and now I'm stumped.
Any ideas anyone?

---

### Post by WillCooke on 2005-03-20
[QUOTE=seasidebaz]I'm having a stupid sound problem.
Alerts and stuff like that play through the speakers normally, but when I load up amaroK or xmms nothing will play, and I get an error saying there is no sound system. I recently did a dist-upgrade from warty to hoary and now I'm stumped.
Any ideas anyone?[/QUOTE]
 Have a look to see which output xmms is using (oss or alsa).

Then try the other one!

---

### Post by jimidel on 2005-03-20
[QUOTE=seasidebaz]I'm having a stupid sound problem.
Alerts and stuff like that play through the speakers normally, but when I load up amaroK or xmms nothing will play, and I get an error saying there is no sound system. I recently did a dist-upgrade from warty to hoary and now I'm stumped.
Any ideas anyone?[/QUOTE]

do you try esd (enlightment sound daemon - eSound ) as audio output ?

---

### Post by oracledarren on 2005-03-20
The following is a bit long winded but it should get things going for you.

Using synaptic install alsamixergui if it is not already there.

Whilst in synaptic also check to make sure that polyaudio is installed.

Once you have done that go to a command terminal and as super user

type alsamixergui

and make sure that all of the correct channels are enabled and at a reasonable volume level (about 80%).  Also mute the channel IC958  Output I think

Once you have done that come out of alsamixer and type alsactl store

This stores all of the settings you have just make so that they will still be there the next time you reboot.

After doing all of that select SYSTEM -> PREFS -> MULIMEDIA SYSTEMS SELECTOR and make sure that is set to the one you want to use.

Hopefully that will fix your sounds issues  :grin:

---

### Post by seasidebaz on 2005-03-22
HUZZAH it works again :) although alsa is buggered so using esound
thanks all :D

---

### Post by kb00heda on 2005-03-22
oracledarren: Thanks for the "sudo alsactl store" tip! I was about to get tired of redoing all ALSA-settings at reboot...   :)

/David

---

### Post by emperor on 2005-03-22
gnome-alsamixer is much nicer that the gui version of alsamixer.

---

