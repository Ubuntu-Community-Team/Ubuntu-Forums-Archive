---
title: "Latest Updates broke sound"
date: 2008-05-28
forum: General Help
---

### Post by jimbo99 on 2008-05-28
After applying the latest updates when prompted by the update manager it looks like it broke pulse audio.  Everything worked previously, no changes to sound or sound players were made to the system--only the acceptance of updates from the Canonical servers. After a reboot no sound.  If I switch to OSS sound is back.  Pulse Audio doesn't work.

Shameful, just shameful.

---

### Post by nomizzz on 2008-05-28
I also had this issue with PulseAudio after the new updates.  I fixed it by editing /etc/modprobe.d/alsa-base and adding the old ```
options snd-hda-intel model=acer
``` fix from Ubuntu 7.10 back in... But now my internal microphone has stopped working again.

Oh well, **** happens.

---

### Post by jimbo99 on 2008-05-28
What also went wrong was:

1)  Even though I turned off power management the screen saver, etc, the system now turns my monitor off--even though I explicitely told it not to.

2) The folder counts no longer work.  I am used to seeing the number of items in a folder (displayed after the name).

3) When I go to places and select a removable drive from the list it puts the drive's icon on the desktop.  But if I hit the eject button for a music CD it will also unmount the drive I mounted using the places menu.  As a consequence I will also loose the share name.

4)  When I boot into the OS from a cold start I get a black desktop background without icons.  I have to alt+ctl+backspace and relog in to get my desktop background and icons.

As far as the entry into that file goes, though I have not tried it, it is not supposed to happen.  That's what makes it shameful.  This OS is targetted at the human being and making the mistake is one thing but expecting the average user to add those lines to some config file is just unacceptable.

Also, my board isn't based on the intel chipset and my computer isn't an acer, so I can't see how that will impact me.  How do I find the old copy pre-update mod so I can compare the old and new to see what my settings actually should be?

Also, as I said I can use the sound if I switch to the OSS sound system rather than pulse audio.  So, the sound card works it just no longer works with pulse-audio.  I check the users and groups and ensured that the username is still associated with pulse audio--it is nothing there was changed.

---

### Post by Zorael on 2008-05-28
Hopefully [OSS4](http://tinyurl.com/5c6luu) will soon work with PulseAudio. ALSA seems to grow increasingly sketchy. *hides*

See [this page](http://ubuntuforums.org/showpost.php?p=5017453&postcount=2) if you have an Intel HDA card and you want to try the model= approach nomizz mentioned. It works with other cards too, of course, but the list I posted there only contains the snd-hda-intel chipset options. Refer to [FONT="Courier New"]/usr/share/doc/alsa-base/ALSA-Configuration.txt.gz[/FONT] for option listings for other cards.

---

