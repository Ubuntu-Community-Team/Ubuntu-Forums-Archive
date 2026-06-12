---
title: "Sound was messed up, I messed it up more"
date: 2016-10-28
forum: General Help
---

### Post by cmrk on 2016-10-28
I'm on Ubuntu 16.04 LTS 64-bit. I have a Dell XPS 15 9550.

Basically, I always had trouble with the headphones. Sometimes they'd work, other times not, I'd often have to suspend the computer then reawaken it to get them to work.

I got frustrated after months of this and tried some troubleshooting steps I found doing Google searches, which seems to have messed it up more. Now, I don't even have the sound icon on the top bar near the clock, and the regular speakers don't work either (UPDATE: actually the sound worked again, but after trying the headphones it's broken again, and I'm still missing the sound icon)

Here are the commands I ran that worsened it:

* rm -r ~/.config/pulse/
* pulseaudio -k && sudo alsa force-reload
* sudo reboot

then I ran:

* rm -rf ~/.config/pulse/ && pulseaudio -k && sudo alsa force-reload

next was:

* rm -r ~/.config/pulse/
* pulseaudio -k && sudo alsa force-reload

finally: 

* pulseaudio -k && rm -rf ~/.pulse && rm -rf ~/.config/pulse

After doing the above, I still had the sound icon near the clock, but now I had one or two instances of "Dummy Output" in the sound settings where "speakers" or "headphones" would normally be.

After all this, I ran:

* sudo alsa force-unload

This seemed to knock the sound out completely.

Not sure if this matters, but I updated the kernel to 4.6 after all this.

I'd like to at least get back to being normal broken like it was originally, as research tells me that updating the BIOS might fix the headphone issue, and I just did that now.

Any help would be greatly appreciated.

---

### Post by Geoffrey_Arndt on 2016-10-28
Hmm, . . . just installing "pavucontrol" would have been the right move to start troubleshooting with.   So now, reinstall (using synaptic) alsa . . . then pulse . . . . then pavucontrol (aka Pulse Audio Volume Control).

---

### Post by cmrk on 2016-10-28
I have the sound icon back now, and under settings it the output device is "Speakers - Built in Audio" instead of "Dummy Output", so I believe I'm back to normal, just stuck with the original problem. Thank you.

---

### Post by Geoffrey_Arndt on 2016-10-29
Sometimes just plugging and re-plugging the sound jack can enable the headphones and similarly enable external speakers.

---

