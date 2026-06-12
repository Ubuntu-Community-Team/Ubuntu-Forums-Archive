---
title: "Need your help with onboard soundcard conflicting."
date: 2007-09-17
forum: General Help
---

### Post by ROUBOS on 2007-09-17
Hi people,
I have an Audigy 2 zs soundcard which I would like to use. When I first installed Ubuntu it was working fine.
The onboard soundcard is disabled in BIOS. Now the problem is that when I restart the machine the onboard soundcard is the one activated and not the Audigy card.

When I click on the sound control the correct device is selected, but in the alsamixer, I get the VIA 8237 onboard card.
So I read a little and blacklisted the device with no luck.

This is what I entered in my /etc/modprobe.d/blacklist file:

blacklist snd_via8237

Is this correct?
Any other thoughts with something I could try?

---

### Post by ROUBOS on 2007-09-17
OK I just changed:

blacklist snd_via8237

to:

blacklist via 8237

After reboot it works. Don't know if its ok or just a one off thing. Will try some more restarts.

---

### Post by ROUBOS on 2007-09-17
I did a restart and it worked. That change could have fixed it. Time will show

---

### Post by ROUBOS on 2007-09-18
I still get that problem. Anyone have any more thoughts? Anything that might help?

---

