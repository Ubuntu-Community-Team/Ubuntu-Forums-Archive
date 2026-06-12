---
title: "Getting gsynaptic to work"
date: 2007-01-23
forum: General Help
---

### Post by healthpellets on 2007-01-23
Ok, I followed [this thread]("http://ubuntuforums.org/showthread.php?t=288970&highlight=gsynaptic"), post #3, and still cannot get gsynaptic to work.  

I get the following error message when I try to run gsynaptic:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

Per the above-linked post, SHMConfig is set to true in xorg.conf.  So what is XF86Config and what do I need to do with it to get this darn program to run?

Thanks!

---

### Post by mayonaise15 on 2007-01-24
The tutorial from the link above actually has the option "SHMConfig" gets a value of "on" instead of "true".  Have you tried both "on" and "true" ?

>         Option          "SHMConfig"             "on"

---

### Post by healthpellets on 2007-01-24
You' are amazing!!!!!!

That worked...and I'm sorry for not being able to fix this myself.  But i'm learning so much in the process.

---

### Post by mayonaise15 on 2007-01-24
Hey, no problem.  I've beaten my head against several walls :roll:

---

### Post by Michl on 2008-03-19
Neither "on" not "true" work for me.

---

### Post by 0guzhan on 2008-06-13
> **Michl said:**
> Neither "on" not "true" work for me.

I have such a problem too. 

The given part of xorg.conf is using synaptic driver not for GSynaptic :S Or I misunderstood something. 

On the other hand; it helps to open Touchpad; but without gsynaptic driver, my touchpad works slower and useless:( 

All in all, i meant can anyone help me to use GSynaptic...?

Thx 4 all, everyone...

---

### Post by Schmeal on 2008-07-09
I'm having the same problem and have seen multiple threads that go unsolved (makes me worry). I have tried many different changes to the xorg and have come up with these observations.

-Adding InputDevice     "Synaptics Touchpad" to the "configured mouse" section = will not restart
-using "true" in SHMConfig does nothing
-using "on" in SHMConfig will not restart

This is driving me crazy, has anyone solved this problem?

(Toshiba 5205 with cpad running HH kubuntu)

---

### Post by jonlemur on 2008-07-12
I think editing the xorg.conf file by itself (no gsynaptics) would be better.  With synaptics (not synaptic) installed, you can 'man synaptics' to see all of the touchpad options you can configure in the xorg.conf file.  This gives much more customization than gsynaptics gives.  

On a side note, I'm pretty sure I ran gsynaptics without any problem a couple days ago to see what I could do with it again, but I tried it again just now and I got the same error message about SHMConfig.  So I wonder if it was a bug with an update.  According to the man pages, SHMConfig is a boolean variable, so "On" "True" and "1" should all function the same.

---

