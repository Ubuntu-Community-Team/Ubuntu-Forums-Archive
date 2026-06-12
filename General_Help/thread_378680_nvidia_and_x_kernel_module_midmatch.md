---
title: "nvidia and x kernel module midmatch"
date: 2007-03-07
forum: General Help
---

### Post by omrsafetyo on 2007-03-07
Hey, I recently installed the latest nvidia drivers using Envy.  Now it seems I have done something terribly wrong.  

When I restarted the X server, it didn't load back up.  Here is the log:

```
API mismatch: the NVIDIA kernal  module has the version 1.0-9746, but this X module had the version 1.0-8776.  Please make sure that the kernel module and all NVIDIA driver components have the same version.
```

I needed to use "linux noapic nolapic"  to boot successfully into recovery mode - but this is where I am stuck.  How do I roll my driver back - or, preferentially - update the x server module to match the nvidia driver?

---

### Post by Waappu on 2007-03-07
Hi

Download and isntall envy and use that to install latest nvidia drivers. That will fix that problem.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by omrsafetyo on 2007-03-07
I think you misread the first line of my post.  :)

---

### Post by Waappu on 2007-03-07
> **omrsafetyo said:**
> I think you misread the first line of my post.  :)

Hi

Yes I did, sorry :( . But did you try run envy again ? After kernel updates you need install nvidia drivers again

---

### Post by Shatrat on 2007-03-07
try uninstalling the linux-restricted-modules-$(uname -r) package and then reinstlal the nvidia drivers.

---

### Post by OffHand on 2007-03-07
Step 2, Option 2

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

---

### Post by omrsafetyo on 2007-03-08
I managed to resolve this issue.

**apt-get remove nvidia-glx**
This actually caused more harm than good.  I then had no Nvidia drivers at all.  

**apt-get install nvidia-glx**

Back to my original bad state

Re-ran envy yet again.  This time, it seemed to work - though soemthing did fail at start-up (more details when I'm at home).

When I get home, I will try to check what drivers my GPU is using - and then I will have to try to figure out what version x server is using.  Can anyone tell me the best commands for doing this?

---

### Post by watson540 on 2007-03-08
dude all that means is what they already said. you gotta re compile the driver with every lernel update. what happens is its seeing part of the module the nvidia installer made for you and then it sees the other stale module thats there from installing nvidia-glx. you have to remove nvidia-glx if you're going to be using envy+nvidia, if you keep it on there you're in for a world of lockups and driver mismatches

---

### Post by omrsafetyo on 2007-03-08
So are you saying I should not have re-installed the nvidia-glx after removing it?

Or are you saying that despite what I did do, the envy script fixed it the second time I ran it...

---

### Post by watson540 on 2007-03-08
well i never used envy so i cant tell you but i was just trying to say you have to use one or the other. it might not even build right if the nvidia-glx package is still on your system so you should remove it prior to installing the driver via envy

---

### Post by wilberfan on 2007-03-09
> **Waappu said:**
> Hi

Download and isntall envy and use that to install latest nvidia drivers. That will fix that problem.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Oh, man, are you ever RIGHT!  
The restricted module upgrade killed my X-server (natch).   My attempt to manually install the very, VERY latest nvidia driver (just released on the 7th?) totally boogered my X...  (Worked fine on my main box...)

Envy didn't do so good the first time I tried it from gnome -- but in desperation, I tried an option '6' (from a TTY terminal)--which is supposed to remove "all things NVIDIA"(?).   I then asked envy to install the NVIDIA driver -- which it did beautifully!   :guitar: 

Man, envy is AWESOME!

---

