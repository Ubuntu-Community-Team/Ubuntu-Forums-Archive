---
title: "Configure to ignore key-presses from TV card?"
date: 2007-07-29
forum: General Help
---

### Post by kris_a on 2007-07-29
Hello,

Since I installed a TV card in my pc recently for MythTV I have been getting random keypress events showing up from the card, this is from my syslog:

Jul 29 13:05:05 ubutudesk kernel: [35455.890094] Pinnacle PCTV: unknown key: key=0x35 raw=0x35 down=1
Jul 29 13:05:05 ubutudesk kernel: [35455.998030] Pinnacle PCTV: unknown key: key=0x35 raw=0x35 down=0

The annoying thing is that this shows itself as a press of the up arrow in whatever application I'm using at the time, and is most annoying when I'm watching MythTV, as the up arrow skips back by 5 minutes :(

Anybody know how to configure Ubuntu to ignore this keypress?  I've been reading the posts but nobody has described anything similar (that I can find).

Searching Google finds no solution, it does seem to be a known problem with the driver, but the only suggestion so far is to remove the card...

Any help much appreciated!
Kris.

---

### Post by kris_a on 2007-07-29
OK a small update...

After checking my logs it seems that the input from the TV card is set up as:

/class/input/input4

Is there some way I can disable this being set for the card?

---

### Post by kris_a on 2007-08-01
*** Bump ***
No ideas anybody?

---

### Post by PaDV on 2007-08-20
Looks related to [https://bugs.launchpad.net/ubuntu/+bug/69555](https://bugs.launchpad.net/ubuntu/+bug/69555).

---

### Post by kris_a on 2007-08-31
Thanks PaDV, I guess your google-fu skills are better than mine :)

The solution is to put the following in /etc/modprobe.d/options

options saa7134 disable_ir=1

Thanks everyone who looked, I can't believe it was so simple.

Kris.

---

