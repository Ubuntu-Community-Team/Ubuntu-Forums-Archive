---
title: "No sound from minecraft in xubuntu 18.04.2 on new PC. Pulse problem diag'd, no fix."
date: 2019-09-08
forum: General Help
---

### Post by jeremybearemy on 2019-09-08
Hi all. Recently built a new PC, installed xubuntu 18.04.2 on it and everything works perfectly except for the fact that I get no audio from Minecraft.

Volume control reports that java is using the wrong sound device, namely the onboard sound, and not the HDMI output where everything else is sending sound.
The correct option is listed but unselectable

I've found a similar question on the forums, and have realised I have the same problem, but the fix they employed didn't work for me.

The problem seems to be that pulse audio has java flagged with "DONT_MOVE" and the fix I found, which was to create a config file with "allow-moves=yes" in the home directory and call it .alsoftrc, didn't work after a reboot.

I have also tried purging and reinstalling java, multimc, and the minecraft instance, all to no avail.

Any help with this would be greatly appreciated

---

### Post by CatKiller on 2019-09-08
The issue is that the panel volume widget  sets the *current* sound device but not the *default* sound device, and Java just grabs the default device.

The PulseAudio Manager (paman) should let you set the default device to be the one that you're using. I've long since moved to KDE (which has its own configuration framework), so it's possible that it was another of the PulseAudio tools that I used, but I'm pretty sure it was that one.

---

### Post by jeremybearemy on 2019-09-08
Thanks, CatKiller, but there's no pulseaudio manager, nor anything similar that I can find in the repos.

Not sure why java is the only thing grabbing the wrong device, as the default IS my hdmi, as far as the volume control app tells me, and everything else is using it as such.

---

### Post by CatKiller on 2019-09-08
Ah. paman seems to have been taken out of the Universe repository for 18.04. That sucks.

You could try installing the 16.04 version. Or figure out the config files to do the same, which is a pain.

I'd really like to think that they took it out of the repository because the GTK configuration utility got sufficiently powerful to handle it on its own but that's... not the way their development has been going.

Sorry I can't offer you a more concrete solution. I experienced it on the GTK side when I was on 16.04 and paman was still available. I went to KDE with 18.04, which uses Phonon to configure PulseAudio.

---

### Post by jeremybearemy on 2019-09-08
Yeah, I don't know how to do either of those things. Been a noob for 12 years, probably be a noob for ever.

---

### Post by CatKiller on 2019-09-08
Well, installing the 16.04 version *could* be as easy as grabbing the [deb file from packages.ubuntu](https://packages.ubuntu.com/xenial/paman) and installing it, or it could be a twisty turny maze of dependencies. More likely to be the former rather than the latter, though; it always struck me as quite a simple application even if I wasn't sure exactly how it worked.

---

### Post by jeremybearemy on 2019-09-08
Thanks again, but this is not the solution. I installed paman, which doesn't seem to allow me to change anything, but it did confirm that my default output device is indeed the hdmi port. I'm looking for a way to remove the DONT_MOVE flag when pulse connects java to an output device.

---

### Post by jeremybearemy on 2019-09-08
Whoops, I was wrong and you were right. I misread paman's interface. The default device was indeed wrong. I used pacmd list-sinks to find the name of the hdmi device, then pacmd set-default-sink to set the correct one. Thank you very much for your help!

Marked as solved.

---

### Post by CatKiller on 2019-09-08
Awesome. Glad my vaguely remembered solution helped :)

---

