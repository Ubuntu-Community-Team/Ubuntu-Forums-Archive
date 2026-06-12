---
title: "Sudden loss of Sound on Ubuntu 12.04"
date: 2014-10-03
forum: General Help
---

### Post by stephane6 on 2014-10-03
I have suddenly lost all audio output on the internet after several  months without a problem. If I check Sound in "system settings" all  the settings (volume etc...) are on yet there is no physical sound happening with or without headphones. I am however still getting audio output on Rhythmbox music player's own  sound control... How do I resolve this problem? or a Terminal command to resolve this very frustrating start to the weekend!

---

### Post by gdesilva on 2014-10-04
The command to use on a terminal is 'alsamixer'. When you run alsamixer, make sure you have selected the correct card (using f6). Once the correct card is selected make sure none of the channels are muted - you will see 'm' on a channel if it is muted. Use tab key to get to the channel which is muted and press 'm' key again to unmute it. If all looks good then I would check the physical connections to make sure everything is plugged in correctly.

Hope this helps

---

