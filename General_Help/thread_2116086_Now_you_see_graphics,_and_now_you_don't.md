---
title: "Now you see graphics, and now you don't"
date: 2013-02-14
forum: General Help
---

### Post by ArlieS on 2013-02-14
Ubuntu 12.10, nvidia graphics hardware. I believe my installation originally worked sanely, but I rarely rebooted or undocked. 

Then I got the crazy idea of installing some nvidia driver. All worked well until the next reboot, whereupon as soon as I logged in, I got a graphics screen - with no menu bar, no way to launch anything, and alternate (non-graphic) screens not working.  After a lengthy battle I fixed this by something like:

dpkg -l | grep nvidia
sudo apt-get remove nvidia-whatever

i.e. I removed anything with nvidia in the name. I did not specify "purge". 

Since then, my system tends to come up in a non-graphical state, looking as if it hung in the rc scripts. If I then undock it, it often responds by giving me a graphics login. If I login, it persists in graphics mode when redocked, and correctly uses my 2 external monitors. 

I went to lunch, and came back to find one monitor claiming something about a bad refresh rate and not showing anything else. The other monitor was working, and I was able to use it to do a controlled shutdown. 

It came back to the same pseudo-hang (no graphics at all). I logged into an alternate screen, and saved things like the ps output for later diagnosis. Then i got graphics with the undock/redock hack. 

An hour or so later, I switched to "screen" F1, but when I went back to F7, i had the "hung" rc output, no graphics. I tried the other screens in case I had the number wrong; no luck. Undock/redock fixed this again.  But that isn't reliable(!) and when I resort to hard resets to recover, I'm risking losing my file system. 

Can anyone help me fix this? At least tell me where to find any diagnostic information which might exist?

---

### Post by Yellow Pasque on 2013-02-14
What kind of laptop is it? What it is output of:
```
lspci | grep VGA
```

It kind of sounds like what happens when you install the nvidia driver on an Optimus system...

---

### Post by ArlieS on 2013-02-14
> **Temüjin said:**
> What kind of laptop is it? What it is output of:
```
lspci | grep VGA
```It kind of sounds like what happens when you install the nvidia driver on an Optimus system...

It's a lenovo T430.

```
$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
```Seeing the above makes me wonder why I was/am so sure it's actually nvidia.  I don't see anything about nvidia in dmesg either. 

The graphics setup is kind of fragile - windows 7 regularly bluescreens when told to use both of my monitors. But Ubuntu 12.04 was happy as a clam, as long as I didn't tell it to use the laptop's own screen as well as the dual external monitors. And to the best of my recollection, so was 12.10. (But in both cases, undocking and/or rebooting was a rare event.)

---

### Post by Yellow Pasque on 2013-02-14
/var/log/Xorg.0.log might contain some clues

---

### Post by ArlieS on 2013-02-14
> **Temüjin said:**
> /var/log/Xorg.0.log might contain some clues

That's quite the giant file.

Is it normal to have a large number (345) lines like:

[  5598.977] (WW) intel(0): first get vblank counter failed: Invalid argument
[  5598.994] (WW) intel(0): first get vblank counter failed: Invalid argument
[  5599.010] (WW) intel(0): first get vblank counter failed: Invalid argument
[  5599.027] (WW) intel(0): first get vblank counter failed: Invalid argument
[  5599.044] (WW) intel(0): first get vblank counter failed: Invalid argument

---

### Post by ArlieS on 2013-02-14
> **Temüjin said:**
> /var/log/Xorg.0.log might contain some clues

Other interesting thing - the /var/log/Xorg.failsafe.log from Feb. 11 (Monday) evening has references to nvidia and the glx driver. I think that was the day I had the completely unusable graphics, and managed to get my menu bars back that evening by nuking any nvidia packages. 

Now I'm wondering if one of them was a problem, and another was needed for sane behaviour, since I think I remember finding and removing two packages, after reading bug reports about nvidia drivers with broken dependencies, which installed "successfully" but produced a non-functional system with symptoms like the ones I had at the time.

---

