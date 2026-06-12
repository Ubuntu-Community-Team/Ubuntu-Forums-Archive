---
title: "Suspend instead of Shutdown if overheated?"
date: 2013-07-13
forum: General Help
---

### Post by zoozd on 2013-07-13
Hello,
My laptop has some fan issues. Is there someway to tweak ubuntu into suspending the laptop instead of shutting it down in case it overheated? Or even better, control at what temperature it should suspend? (I'd like to set it to 90 degrees instead of 105).

Processor: Core i5 2.3 GHz 430M.

Please don't suggest ways to decrease the heating, I have already delt with that a lot.

---

### Post by Cheesehead on 2013-07-13
No. Overheat shutdown is done at the hardware level by the BIOS, not Ubuntu.

You can write a script that suspends your system at any temperature you wish...as long as it's below the hardware limit.
The 'lm-sensors' package includes software to easily read the temperature.
Your desktop power manager is compatible with the dbus command to suspend. See the 'd-feet' package for a great tool to learn how to use dbus commands.

---

### Post by tgalati4 on 2013-07-13
Are there any settings that you can change in BIOS?  Perhaps put in a slightly higher temperature (which will shorten hardware life) to give more time for a script to work properly.  Then use dbus commands to monitor temperature and suspend before the hard shutdown.

If this is a laptop, then it's time to pull it apart and replace the heat paste with a higher-quality paste and clean the fans and intakes.

---

### Post by zoozd on 2013-07-13
Hmm, thanks!

I guess I'll be writing my own script then.

And unfortunately no, the BIOS doesn't have such settings.

---

### Post by coldraven on 2013-07-13
If you have pets then clean the fan. Mine was half choked with fluff, now it runs sweet.
I found instructions on how to do it on the interwebs.

---

