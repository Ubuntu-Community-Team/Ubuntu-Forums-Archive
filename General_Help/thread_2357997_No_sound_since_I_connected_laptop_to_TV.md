---
title: "No sound since I connected laptop to TV"
date: 2017-04-08
forum: General Help
---

### Post by Satyros on 2017-04-08
I installed Ubuntu 3 days ago and everything was going great. I watched a movie on my TV the other day, thru an HDMI cable. Ever since then I have no sound on Firefox, Chrome or VLC. Weirdly enough, Spotify does have sound.

If I click on sound settings and test the sound everything works fine. The boot sound is also audible.

Yes, I've checked the applications tab on sound settings. Even if the sound is set to max on that application, still no sound.
Play sound through speakers is also turned on. So I'm at a loss about the next step...

Thank you.

---

### Post by TheFu on 2017-04-08
run **pavucontrol**.  Check that the speakers are the output device for each sink, not HDMI.  Could be that pulse audio still is sending audio out the HDMI port.

If you are running Xubuntu (or one of the non-Pulse-audio using flavors), check with **alsamixer** using F6.

---

### Post by lammert-nijhof on 2017-04-08
Install PulseAudio Volume Control. > sudo apt install pavucontrolThat package has two tabs more then the standard installed Sound Settings. Check which audio device your applications are using now, probably most programa try now to use the hdmi device. Start pavucontrol and select the playback tab, Start your application and look, which audio device that application is using in the "playback" tab of pavucontrol. Use the button to select the right audio device from something with "HDMI" to probably something with "built-in stereo"

---

### Post by Satyros on 2017-04-08
> **lammert-nijhof said:**
> Install PulseAudio Volume Control. That package has two tabs more then the standard installed Sound Settings. Check which audio device your applications are using now, probably most programa try now to use the hdmi device. Start pavucontrol and select the playback tab, Start your application and look, which audio device that application is using in the "playback" tab of pavucontrol. Use the button to select the right audio device from something with "HDMI" to probably something with "built-in stereo"

It was exactly what was happening. Thank you guys! I suppose this will happen every time I connect an HDMI cable. Is there a way to make it not happen, so I don't have to change this manually every time?

---

### Post by TheFu on 2017-04-08
Not that I'm aware without non-trivial scripting.

It hasn't been that big of a deal to me, so I haven't written a script that lists all the sinks, on all the sound devices connected (the order can change), captured the numbers, then set outputs to the expected output device for the time.  

I wasn't using pulse audio (which I consider broken by design, just like systemd) until the last few months - when it became clear I wouldn't have any other choice if I wanted audio to work.

However, on my laptop, if I remember to toggle the enable/disable HDMI screen cloning using the function keys before AND after I'm done, I suspect it would work just fine. No proof of that, just suspicion.  It does go back to normal after a reboot ... and since I only mirror over HDMI when giving presentations and it seems to work then ...

---

### Post by Satyros on 2017-04-09
Connected the laptop to the TV the other night and it didn't happen again.

---

### Post by lammert-nijhof on 2017-04-12
No the system remembers your choices, but you might have to do it for other applications too.

---

### Post by Brackenn on 2017-04-20
I'm having the opposite problem, I upgraded the tv, and the new one has no VGA+sound port anymore, just HDMI, and now my Video server computer can't seem to play sound through the HDMI port on the ASUS Video card. There isn't some other hookup from the motherboard to the video card, is there? The sound comes through the PCI slot, right?

---

### Post by lammert-nijhof on 2017-05-01
If you have a video card with HDMI and you connect it to a new TV, there is a fair chance that the software will provide the sound through your hdmi interface. If you don't like it, select the source of sound you want in the playback tab of the Pulseaudio Volume Control. See my previous suggestion a few posts back.

---

