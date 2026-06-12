---
title: "Will Not Boot Without Recovery Use?"
date: 2013-04-11
forum: General Help
---

### Post by arsenic_creed on 2013-04-11
Okay, this is weird, sort of hard to explain, and, I'm sorry, but I have no idea what I did to mess it up...
Day before yesterday I did the same stuff I do on my computer every day, installed some updates they told me I needed, and shut down normally. The next day the computer wouldn't boot to my Ubuntu (I've got a dual boot) so I ran clean packages in the recovery mode (thinking that maybe one of the updates didn't like something else I've got in) and it booted fine after that. (Once immediately from the recovery mode with the video all weird and huge, the second time just a normal restart from there).
Today, it's doing it again and I've just noticed something weird. If I try to boot the way I normally do the screen goes purple (the way it does pre-login screen loading), then goes black and just sits there. If I use clean packages now, it will boot right after the recovery console but still not normally. If I go into the recovery console and hit 'resume normal boot' without even doing anything else it boots from there (but still not just normal boot without opening the recovery console).
So, in summary, I can only boot from recovery mode and it does say that some video drivers may fail without the full boot but I haven't done anything to my video drivers at all so is that even a possibility? How do you even check for drivers on Ubuntu?
[I've got a Windows 7 and 12.10 dual boot {both 64 bit} ]
That's a bit long-winded and I apologize. I just wanted to try and get all the necessary information on there.

---

### Post by grahammechanical on 2013-04-11
> [COLOR=#000000]it does say that some video drivers may fail without the full boot[/COLOR]

That gives us a clue. When we use Recovery Mode>Resume the video driver does not get loaded and we are using the open source Nouveau driver.

Try experimenting with video drivers. In 12.10 it is System Settings>Software Sources>Additional drivers tab.

Regards.

---

