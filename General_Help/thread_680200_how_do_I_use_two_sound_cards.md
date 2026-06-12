---
title: "how do I use two sound cards?"
date: 2008-01-27
forum: General Help
---

### Post by goodmanbrown on 2008-01-27
I installed a sound card in addition to my on-board sound.  The new card is an M-Audio Audiophile 2496.  I want to use the Audiophile to experiment with audio recording, so I have it hooked up via a mixing board to a microphone.  For reasons having to do with power-saving and convenience, I'd like to be able to unplug the mixer when I'm not recording, and use the on-board sound for daily music-listening purposes.

Some threads in these forums indicate that it shouldn't be hard to use two different sound cards, and switch between them as needed.  But I'm new enough to this that I'm embarrassed to say that I don't understand the System->Preferences->Sound dialog.

Short Version:  I want to have my on-board sound be the default.  At times when I want to record, I'd like to switch over to my Audiophile card so I can use the mixer and mic.  Is System->Preferences->Sound the place to make this switch?  If so, where in the dialog do I actually make the switch?

Thanks for your time!

---

### Post by goodmanbrown on 2008-01-28
OK.  I looks like I was on the wrong track entirely.  Here's what I now think is the way I should be doing this.  If you have a better idea, let me know.  (Most of this information came from an [Ubuntu Studio prep page]("https://help.ubuntu.com/community/UbuntuStudioPreparation").)

When I record, I use jack, and only when I record do I use jack.  So my new strategy is to set jack to use the Audiophile sound card, while leaving everything else to use the default, which is the onboard card.  This is a two-step process.

1) Define which card is the default, so that Ubuntu doesn't get confused.  First, find out what modules are driving your working sound cards:

```
cat /proc/asound/modules
```

My output looks like this:

```
 0 snd_intel8x0
 1 snd_ice1712
```

Now edit the alsa modules list to define which card to use as the default.  (The first, or 0th card is the default card.  In my case, I want the intel8x0 to be the default.)

```
sudo gedit /etc/modprobe.d/alsa-base
```

And add the following lines to the end of the file.
```

options snd_intel8x0 index=0
options snd_ice1712 index=1
```

At this point, my onboard sound should dependably be index 0, which is the default, and my Audiofile card should dependably be index 1.  So...

2) Configure jack to use the Audiophile card.

It is easy to use qjackctl to do this.  Just run it, click the "setup" button, and in the settings dialog, set both "Input Device" and "Output Device" to "hw:1"

So far this seems to be working for me.  I successfully loaded jack+ardour, recorded a quick session, exported it to wav, then shut down jack and ardour and listened to the wav file through my on-board card.  I'm open to better ways, but for the time am satisfied.

---

