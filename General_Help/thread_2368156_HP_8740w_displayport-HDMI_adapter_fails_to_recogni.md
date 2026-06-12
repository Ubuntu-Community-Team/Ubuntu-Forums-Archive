---
title: "HP 8740w displayport-HDMI adapter fails to recognize digital audio stream"
date: 2017-08-07
forum: General Help
---

### Post by mrzenwiz on 2017-08-07
I recently bought a refurbished HP 8740w elitebook, on which I run Xubuntu 16.04.3.  I have two DP-HDMI adapters so I can connect to my 40" HDMI TV to watch movies on.  However, I get no sound through the connection at all.  I have the standard Xubuntu ALSA and pavucontrol both installed and they work in every other respect.

I tested this with the Windows 7 that came with the notebook, and it handles video and sound perfectly.

However, Xubuntu refuses to recognize the digital audio stream.

Previously when I would connect the TV to my HP 8710w (which had an HDMI connector), pavucontrol would show two analog audio options, two digital audio options, and an analog input audio option.

Now it only shows 5 different analog audio options, no digital at all, and of course nothing comes through to the TV.

HP doesn't support any non-native OS, so they won't help.

How do I get the sound to work?

---

### Post by Autodave on 2017-08-07
Did you install the Linux driver for that card? If not, you need to do so. The Softwar Center or Synaptic will have it. According to Nvidia's website, you need the 304.102 driver for that card.  Alternately, you can go to Settings -> Additional Drivers and install the one that is recommended.  After you get the correct driver, you will then be able to see (and choose) in pavucontrol, the sound output from the video card.

---

### Post by vocx on 2017-08-07
> **mrzenwiz said:**
> I recently bought a refurbished HP 8740w elitebook, on which I run Xubuntu 16.04.3.  I have two DP-HDMI adapters so I can connect to my 40" HDMI TV to watch movies on.  However, I get no sound through the connection at all.  I have the standard Xubuntu ALSA and pavucontrol both installed and they work in every other respect.
...
I don't want to discourage you but there seems to be some bugs when it comes to getting HDMI audio correctly when you have an Nvidia card.

See this thread: [https://ubuntuforums.org/showthread.php?t=2367135&p=13670073#post13670073](https://ubuntuforums.org/showthread.php?t=2367135&p=13670073#post13670073)

You should definitely install your restricted drivers, if any, and try to activate HDMI audio. However, my gut feeling is that the problem is in the Linux drivers, so unless Nvidia themselves really sort out the problem, the HDMI audio may not truly work no matter what you try.

Just a note. Don't buy a DP to HDMI converter. Just buy a cable with a DP plug on one side and an HDMI plug on the other. Better to use a single cable instead of having multiple connectors and adapters.

---

