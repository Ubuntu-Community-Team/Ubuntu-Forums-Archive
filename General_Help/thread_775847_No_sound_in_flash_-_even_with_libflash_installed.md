---
title: "No sound in flash - even with libflash installed"
date: 2008-04-30
forum: General Help
---

### Post by duojet on 2008-04-30
So, I upgraded from K6.06 to K8.04 and I've been having this problem with flash, I can't get any sound. I have installed and uninstalled so many packages I just gave up and reinstalled from the cd (using my old home partition)I'm not the only one here like that, I'm sure, so any workarounds would be great.

Right now I have libflash-support and gnash UNINSTALLED. I've tried both before and it seems to be no joy at the moment. I'm still using my old home directory from 6.06 so I could be having a problem with one of the config files. 

any ideas?

please?

---

### Post by duojet on 2008-05-01
HAH! HAH!

I Fixed it!, after some poking around on teh interwebs, I found a bug report that directed me to delete .asoundrc and .asoundconf
Alsa created new files, now everything is golden!

---

