---
title: "New Hardware, Audio and Screensaver"
date: 2013-04-06
forum: General Help
---

### Post by oakridge on 2013-04-06
For some time the Ubuntu machine has been getting slower and slower and more and more unreliable which pointed to a hardware problem.  I was lucky enough to spot a power supply tester in Maplins which instantly showed up the problem; the power supply was terminally ill.  A new power supply was fitted and pretty well everything is super fast and generally hunkydory.  

Except there is no sound, yes it is plugged in, turned on and in the right hole.  It worked perfectly before.

Also, I was trying to set Xscreensaver before the hardware upgrade to display photographs from a directory, but failed.  It is set to: 'Only One Screensaver', 'GLSlideshow', on the Advanced tab 'Choose Random Image' and it points to the correct directory.  A two line message does come when the screen blanks but the text is tiny and only there for a short while.  I have looked at a few other posts on this subject but have not managed to get it working yer.

Am I allowed two questions in one?

Thank you.

Malcolm

---

### Post by dabl on 2013-04-06
It seems highly doubtful that the PSU replacement had any affect on either the sound or the video hardware, assuming the interface to the motherboard is correct, so I would treat these issues as unrelated to the new PSU.

Here's your audio troubleshooting guidance:  [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

As it says, in a terminal:

```
cd ~/
  wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh

```

---

### Post by oakridge on 2013-04-08
Thank you for your reply dabl.

The reference from alsa is here:

[http://www.alsa-project.org/db/?f=777de80e07296c0d568f5bd16389e00a47d5a628](http://www.alsa-project.org/db/?f=777de80e07296c0d568f5bd16389e00a47d5a628)

It is just strange that the sound worked immediately before the change and not after.  It is a job we have done many times since 486 days.

The xscreenserver problem is different and I will make a separate post in due course.

Thank you

Malcolm

---

### Post by dabl on 2013-04-08
Disclaimer -- I am not an ALSA audio expert.

Nothing jumps out of your script output as "wrong".  You need to be using "card 0", and the analog channel.  I'm a KDE user so some things are different on that desktop, but I think pavucontrol is pretty much the same.  So on the "Configuration" tab, you need to choose "Built-in Audio", and the profile is "Analog Stereo Duplex".  Set the digital controller to "Off", and also any other choices that appear on that tab.

On the Output Devices tab, you want "Analog Output" and turn up the volume reasonably.  If you have a Gnome volume control or mixer, make sure it is not muted and turn it up as well.  Double-check power to speakers, and any manual speaker volume knob (don't laugh, I've had overnight visitors adjust mine when I was away).

---

### Post by oakridge on 2013-04-09
Cracked it!  But I don't actually know how which isn't terribly helpful.  I looked at everything  that had anything to do with sound, poked and prodded and found that sound came.

Thank you for your help.  I suppose it must have been some senior moment of mine.

Malcolm

---

### Post by dabl on 2013-04-09
Good! -- yep sometimes the ways of ALSA and pulseaudio are a bit more mysterious than they really should be.

Thanks for adding "SOLVED" at the beginning of the original title in case it might help someone else.

---

