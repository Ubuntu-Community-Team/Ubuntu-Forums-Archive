---
title: "Ubuntu 14.04 laptop dim issue"
date: 2014-06-19
forum: General Help
---

### Post by Pshemas on 2014-06-19
I've installed 14.04 and in general most of things seem candy-dandy :) . I'm running Ubuntu on Lenovo Ideapad Y580 with Nvidia Optimus card (Intel HD4000 / Geforce GTX 660M ). I've noticed one annoying thing - when the latpop runs on battery the screen dims after a couple of seconds. Tried to disable it on the brightness panel but it did not help - the screen still dims even though this option is checked off.
Tried dconf - went to **org -> gnome -> settings-daemon -> plugins -> power**. But this option is unchecked there as well - also I've noticed there are no options to set time for dimming.
Searched online for solution but haven't found one.
Any ideas howto fix this? It's rather annoying.

---

### Post by pretty_whistle on 2014-06-19
See if "Light Locker Settings" in the Software Center solves it.  It worked for me.

---

### Post by Pshemas on 2014-06-22
@pretty_whistle:  thx, but that didn't help - and to be honest I did not expect to do the trick as far as I can tell this app handles screen powering off and locking not dimming.

I did some tweaks and finally the screen stopped dimming after a couple of seconds - but got to admit as I've been doing the changers in rather chaotic way I'm not sure what has helped. I'd bet that it was changing the settings on "Nvidia X Server Settings".

---

### Post by jona26 on 2015-05-08
@Pshemas - Would you mind mentioning a few things that you've tried? I'm having the same issue. 14.04 on a Samsung ATIV Book 4.

---

