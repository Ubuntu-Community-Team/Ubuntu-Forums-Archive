---
title: "wrong sound card after suspend/resume"
date: 2013-09-27
forum: General Help
---

### Post by ulrichmuc on 2013-09-27
In the sound preferences menue I see under hardware
   Built-in Audio and CM106 Like Sound Device (my USB-SoundCard)

under Output
  Built-in Audio and CM106 Sound Device Digital Stereo

I select CM106 and everythig works fine.

However, after suspend/resume the built-in sound card is selected.

Is there a command-line way to adjust the sound preferences, that I can put into some script in /etc/pm/sleep.d ?

---

### Post by Kirboosy on 2013-09-27
I imagine that the cause is due to the computer sleeping the USB sound card disconnects. It takes the USB device a second to reregister upon waking up. Because of this Ubuntu can't find it upon waking up and reverts back to the internal sound card. 

You may wanna check in your BIOS and see if you can disable the onboard sound card.

[UbuntuStudio/USBAudioDevices]("https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices")

Hope that helps!
~Caboose

---

### Post by ulrichmuc on 2013-09-28
> **Caboose885 said:**
> I imagine that the cause is due to the computer sleeping the USB sound card disconnects. It takes the USB device a second to reregister upon waking up. Because of this Ubuntu can't find it upon waking up and reverts back to the internal sound card. 

You may wanna check in your BIOS and see if you can disable the onboard sound card.

[UbuntuStudio/USBAudioDevices]("https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices")

Hope that helps!
~Caboose

I agree with the diagnosis, but not with the solution. I don´t want to fiddle with bios whenever I use the notebook withot the USB-soundcard, i.e., when I am tavelling.

It is easy to correct the sound settings manually via the GUI. But there must be a command line way to do it, which then could be automated.

---

### Post by Toz on 2013-09-28
You might want to have a look at setting up udev to manage the insertion/removal of the device, specifically to set it up as default. I'm unable to test this, but the perhaps the following links may help:
- [http://askubuntu.com/questions/95632/volume-widget-issue-with-sound-card-hotplugging]("http://askubuntu.com/questions/95632/volume-widget-issue-with-sound-card-hotplugging")
- [http://alsa.opensrc.org/Udev]("http://alsa.opensrc.org/Udev")

---

### Post by Kirboosy on 2013-09-28
Have a look at this link.

[How do I change the device from the command line?]("http://askubuntu.com/questions/14077/how-can-i-change-the-default-audio-device-from-command-line")

Hope that helps!
~Caboose

---

### Post by ulrichmuc on 2013-09-29
> **Caboose885 said:**
> Have a look at this link.

[How do I change the device from the command line?]("http://askubuntu.com/questions/14077/how-can-i-change-the-default-audio-device-from-command-line")

Hope that helps!
~Caboose

Well, this is helpfull.

However, I tried to put pacmd-lines into a script in /etc/pm/sleep.d to be executed on resume, but I get 

    "No PulseAudio daemon running, or not running as session daemon."

Is there another place to put this script?

ulrich

---

### Post by Kirboosy on 2013-09-30
You could try putting at the top of your script
```
**SLEEP 10s**
1. s for seconds (the default)
2. m for minutes
3. h for hours
4. d for days
```

That would tell the script to wait 10 seconds before running the rest. That might be enough time to let everything come back to life. You might have to play with the times though

~Caboose

---

### Post by ulrichmuc on 2013-10-01
> **Caboose885 said:**
> You could try putting at the top of your script
```
**SLEEP 10s**
1. s for seconds (the default)
2. m for minutes
3. h for hours
4. d for days
```

That would tell the script to wait 10 seconds before running the rest. That might be enough time to let everything come back to life. You might have to play with the times though

~Caboose

No, timing is not the problem. The solution is as follows:
I put the script into /usr/lib/pm-utils/sleep.d and name it in a way that it is executed after 01PulseAudio.
The script contains

  case $1 in
     resume)  sudo -s -u <user>  HOME=/home/<user> /home/<user>/bin/usb_sound ;;
  

where <user> is the acount under which pulsaudio runs and usb_sound contains the pacmd lines which do the real work

ulrich

---

### Post by Kirboosy on 2013-10-01
Ah cool, glad you figured out how to get it working. Very useful information to know.

If that solved your problem please mark this thread as "solved" (under Thread tools)

~Caboose

---

### Post by ulrichmuc on 2013-10-01
> **Caboose885 said:**
> Ah cool, glad you figured out how to get it working. Very useful information to know.

If that solved your problem please mark this thread as "solved" (under Thread tools)

~Caboose

It solves my initial problem, so I´ll mark the tread solved.

A remaining problem is that the equalizer pulseaudio-equalizer-gtk gets into disabled state and needs some action to become enabled again.
But this is a different topic.

ulrich

---

