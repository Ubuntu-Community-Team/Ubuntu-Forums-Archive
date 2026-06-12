---
title: "PulseAudio fix for Skype &amp; autostart"
date: 2014-01-26
forum: General Help
---

### Post by la_monda on 2014-01-26
Greetings to the community. I am trying to setup skype for my mothers laptop in xubuntu 13.10 x32bit.
Sound output wasn't working for skype but luckily i stumbled on this solution:
[COLOR="#FF0000"]If you are packaging Skype for your distribution, you need to change the Exec line in your Skype .desktop file as follows:

Exec=env PULSE_LATENCY_MSEC=60 skype %U

If you are a user, and your distribution doesn’t already carry this fix (as of about a week ago, Ubuntu does, and as of ~1 hour from now, Gentoo will), you need to launch Skype from the command line as follows:

$ PULSE_LATENCY_MSEC=60 skype[/COLOR]

Through terminal i managed to launch skype by using this command: **PULSE_LATENCY_MSEC=60 skype** (different from the suggested) and skype DID worked!
However i want to add skype to the autostart programs list and i tried several things and neither of them worked.
I changed the command from the shortcut of the application skype %U to the one suggested and nothing changed, I changed the command to the one that worked in the terminal and actually still nothing.

Since through the terminal command it actually works, can't i make an autostart entry for that terminal command (by making an executable script file and puting it to autostart??? - don't now how though :confused: ) in order to launch skype upon login?
Thanks in advance for the support!

---

### Post by ajgreeny on 2014-01-26
The skypestart.sh script would be
```
#!/bin/bash
PULSE_LATENCY_MSEC=60 skype
``` and then point to the script in the pathway for autostart, ie, if it's in your home /home/username/skypestart.sh

But you could also try using the complex command in autostart
bash -c "PULSE_LATENCY_MSEC=60 skype" to see if that works.

---

### Post by la_monda on 2014-01-26
thanks, I will try these and let you know how it goes

---

### Post by la_monda on 2014-02-14
this command worked: env PULSE_LATENCY_MSEC=30 skype %U

---

