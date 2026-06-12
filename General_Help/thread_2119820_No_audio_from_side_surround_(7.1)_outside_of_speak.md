---
title: "No audio from side surround (7.1) outside of speaker test."
date: 2013-02-24
forum: General Help
---

### Post by satsun on 2013-02-24
I have a Creative X-Fi Titanium PCI-E card and am using Ubuntu 12.10 64bit.  It is setup to output 7.1 channels to an external receiver using the analog outputs; it works in Windows and to a certain extent it works in Ubuntu.

In Ubuntu, when I test the speakers from the GUI it goes around and properly matches up each speaker; same for when I do speaker-test -c8.  However, when in games or when playing a movie with a discrete 7.1 audio track, I get no audio from the side speakers.  The side speakers are what makes a 7.1 setup so it seems like for everything other than the speaker test, I'm stuck in 5.1 mode.

I have dug around in the /etc/openal/alsoft.conf and the /etc/pulse/daemon.conf and have played with the settings but have been unsuccessful at getting discrete output working.  What has made the sides work is enabling upmixing in the daemon.conf but I find upmixing a bit annoying because it makes stereo sources fill all speakers.

Are there any other configuration files associated with audio configuration that I might be overlooking?

Thanks.

---

### Post by meteorrock on 2013-02-25
Are your speakers powered and wired into the sound card ? Try plugging in your  other speakers and check the settings in the audio settings for ubuntu.  You might need to look online for some sort of third party tool for speaker setup past 5.1, ubuntu only handles 5.1 channels out of the box.

Check this site here on setting up ALSA for ubuntu and how to set it up. [http://alsa-project.org/main/index.php/Matrix%3AMain](http://alsa-project.org/main/index.php/Matrix%3AMain)

---

