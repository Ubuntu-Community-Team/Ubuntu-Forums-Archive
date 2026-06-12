---
title: "Not dissabling touchpad for hinged Dell 3147"
date: 2015-02-02
forum: General Help
---

### Post by Su_Heng on 2015-02-02
Hi all,

   I purchased one Dell 3147 and installed Ubuntu on it. However, when I fold the laptop to tablet mode. The keyboard is disabled automatically. However, the touchpad is still enabled.


   That's so weird, does it mean keyboard disabling is hardware controlled but touchpad isn't? This is unacceptable!


How can I make it work in Ubuntu or other linux distribution? Please help

Best Regards,
Steven

---

### Post by ajgreeny on 2015-02-02
If it's a synaptics touchpad you can use command **synclient TouchpadOff****=1** and then **synclient TouchpadOf****f=0** to turn it on again.

You imagine could add those commands to scripts, with launcher icons so that you can just touch them to run the script, but I have no knowledge of ubuntu touch, nor exactly how it works so I may be wrong.

---

### Post by Su_Heng on 2015-02-03
Hi Ajgreeny,

   Thank you so much!  Yes, I know it does work. However, is there anyway to do it automatically? Like how can I register a mode listener to get call back while the tablet mode is active so I can trigger my script to disable / enable ?
   BTW, I am thinking it's driver issue of dell mother board driver for linux but not touch pad driver issue, am I right?

---

