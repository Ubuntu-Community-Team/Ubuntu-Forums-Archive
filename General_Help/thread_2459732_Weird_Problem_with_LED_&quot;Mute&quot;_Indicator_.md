---
title: "Weird Problem with LED &quot;Mute&quot; Indicator after Resume from Suspend ??"
date: 2021-03-24
forum: General Help
---

### Post by GhX6GZMB on 2021-03-24
I have a laptop running 20.04 LTS and it runs perfectly. But I have one issue:

Between screen and keyboard there's a touch panel for turning on/off WLAN and controlling audio volume. Also a touch button for muting audio. This one's my problem.

After a normal boot, all buttons work perfectly. But after a Suspend (and also Hibernate) Resume, the "Mute" LED is out of control.

It is on, but audio is not muted. Pressing it to turn it off works, but it turns on again after one minute. It's function is also inverted compared to normal mute operation.

Now here comes the really weird part: opening a browser window  and playing some Youtube video, the LED works normally again. Closing the Youtube window makes it revert to the abnormal behaviour.

I suspected Pulseaudio, but its working correctly when playing a video led me away from this (although it's still a possibility).

Some setting is left "hanging" after a Resume, but I'm at my wit's end.

Any idea is highly appreciated, please help.

*_Thank You._*

PS: just to rule out HW issues: I have two identical laptops with 20.04 (one English, one German), and they both behave this way.

---

### Post by guiverc on 2021-03-24
I have no real ideas sorry, I've not experienced this before.

You haven't said if you're using the GA (5.4) or HWE (5.8) kernel, and if it was me, I'd try using the other kernel option.  If you don't want to install it, you could also try booting different *live* media (eg. Lubuntu 20.04 or 20.04.1 media for GA/5.4 kernel, and Lubuntu 20.04.2 media for HWE/5.8) and see if there is a difference.  

Using the *live media *I would test for the issue you are describing, does it occur there? (esp. using the same kernel you are using, 5.4 or 5.8 anyway).  If it doesn't occur there, I'd likely (back to your installed system) explore any older kernels you have installed (*though I suspect you've tried this, is this issue new? a recent install? or was noticed after a change? your not mentioning details of this implies to me you've ruled it out; is this true?)*

The weird part: browser changes behavior, is likely a huge clue, but which browser?  Is it a specific browser (eg. firefox), but not others (chromium, falkon, tor-browser etc) or all of them. If you haven't tried others, I'd for sure try them, and then I'd likely look at the *dep-rules* (ie. *what libraries*) are used by that browser and hope i see clues from that.

I'd also try an external keyboard; if that keyboard is impacted too, it'll likely mean it's easier for others to re-create the issue and less specific to your laptops (are they different makes? models?) and I suspect will be easier to chase down. If it's only laptop keyboards, I suspect it'll be harder as is I suspect more  likely make/model specific

---

### Post by GhX6GZMB on 2021-03-25
guiverc, Thank You for your response.

I can rule out the kernel, this issue persists since Lubuntu 19.10 (my first Lubuntu install).
I can also rule out the browser. I have the issue on two machines, one with Opera, the other with Firefox.

Something goes wrong when Resuming.
Only a few settings are involved directly here: grub, fstab, initramfs-tools and polkit-1. I'll keep investigating.

---

### Post by GhX6GZMB on 2021-03-26
I've now come to the conclusion, that no driver or configuration file for the "Mute" LED exists for an HP6910p (and other 6xxx series) laptop in Lubuntu, All searches in /etc and /usr have brought up zilch.

My final solution is to desolder the LED (the touch button works perfectly). I don't need it anyway, the Panel speaker icon tells me when it's on.

Sad.

---

