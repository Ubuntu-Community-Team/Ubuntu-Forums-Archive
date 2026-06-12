---
title: "Sound Works...When It Wants To"
date: 2007-08-17
forum: General Help
---

### Post by danthebugman on 2007-08-17
So this little problem has been haunting me since installing Feisty a few months ago.  When I first installed there was sound, but then one day it mysteriously disappeared :(. Baffled I restarted the comp only to have the sound return...then subsequently disappear the next day.  And so it has continued for the past few months.  The sound will work, then it won't, then it will again.  It's becoming VERY frustrating and I would appreciate some help.  Please.

Regards,
Daniel

---

### Post by djxcon on 2007-08-17
First, we need to know more about your sound card(s).  

Are you using hibernate or suspend?  I only ask because my sound card module had issues when returning from suspend.  I now know to unload the module first before suspending the computer which helps.

Do you have on board sound as well as a PCI sound card?  If so, I have seen this type of behavior when there are two sound cards on a system.  If this is the case, you may want to try and disable one of the sound cards via the bios.

Also, to run a quick sound test, try using this command from a terminal:
```
speaker-test -c2 -Ddefault -t wav
``` 

When debugging, I found this command to be very useful.

---

### Post by danthebugman on 2007-08-17
I'm not sure what the sound card is.  Whatever came installed on my laptop, so probably just some generic on board thing.  If it helps my laptop is a Gateway MX7118.  Also I ran that test you suggested and it ran fine, but then I just rebooted not too long ago and my sound is working lol.  Any more suggestions??

---

### Post by djxcon on 2007-08-18
> Also I ran that test you suggested and it ran fine, but then I just rebooted not too long ago and my sound is working lol. Any more suggestions??

When you ran the sound check and it worked, did sound work for other applications?  If not, what application were you using?  

Also, are you suspending the laptop or using hibernate?

You might find additional information about your sound card by looking at System -> Preferences -> Hardware Information.

---

### Post by danthebugman on 2007-08-18
Alright so when I got home this afternoon my sound wasn't working again :mad: so I ran that test again and nothing.  I have no sound in any of my programs (I tired Listen and Firefox as those are the two I use the most), but it was working in all programs yesterday.

The sound card is by ATI Technologies Inc and is a IXP SB400 AC'97 Audio Controller (PCI type).

I have my laptop setup to hibernate when I close the screen and the display is set to suspend when the comp isn't busy for 15 minutes.  These settings are for AC power which is what it is on mostly these days.

---

### Post by djxcon on 2007-08-19
> I have my laptop setup to hibernate when I close the screen and the display is set to suspend when the comp isn't busy for 15 minutes.

From a clean boot, make sure that your sound is working and then hibernate the laptop by closing the lid. After the laptop has completed hibernation, wake it up again.  When it comes back from hibernation, try to play a music file or run the speaker test.  Obviously, the objective here is to figure out if hibernate is causing your sound module to fail.

---

### Post by danthebugman on 2007-08-24
Yeah the sound doesn't even work after a clean boot so no need to try hibernating it yet...
So perhaps my sound card has gone out :confused: or should I try reloading the drivers or something like that??

---

