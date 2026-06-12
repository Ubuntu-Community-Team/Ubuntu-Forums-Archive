---
title: "computer halts on reboot command instead of reboots like it should GUTSY 7.10"
date: 2007-10-30
forum: General Help
---

### Post by nowshining on 2007-10-30
i tried seeing if it's a script problem but it looks like all scripts are in the right place  with sysv-rc-conf, and I tried issuing both a sudo init 0 and sudo init 6 commands.

sudo init 0 - shuts the computer down normally
sudo init 6 - shuts the computer down instead of rebooting ii.

I'm guessing it's a script issue tho. I tried re-installing init and upstart to no sight of seeing my problem disappear. Last time the BUM screwed up the scripts order and re-setting them worked but not now, as i used BUM  to start hald when it didn't work or startup which it is so far.

Any help will be thanked for helping me fix this.
Also I did the upgrade from feisty to gutsy and so far I've fixed other issues and it seems like this is the only one remaining in the end. :/

---

### Post by AlexThomson_NZ on 2007-10-30
It's not the same as the similar sounding problem in the sticky "Gutsy Known Bugs and Workarounds" is it?

---

### Post by nowshining on 2007-10-30
no the reboot worked fine until I used BUM which put them out of order and last time I got it fixed by re-setting the scripts to their rightful positions. Which now seems odd as they look to be in the right place, I can press ctrl + alt + delete quickly before it somehow halts and it reboots fine if I do that sequence of keys before it tries its halt thing.

OR it could of been when I deleted something out of /var/cache - most likely but I've removed things back that I deleted and so far so good on everything else. :/ that's the only remaining problem I am having and fixed the rest.

I even tried removing the X and replacing it in sysv-rc-conf but still nothing.. I still believe the items from /var/cache are in the root trash folder but I do remember restoring pretty much everything needed back into their rightful positions..ugh..!!!!

---

