---
title: "No sound after re-install"
date: 2008-07-04
forum: General Help
---

### Post by tj.brewster on 2008-07-04
HI been a linux use for about three weeks now.  Installed Ubuntu first, everything worked out of the bok.  Got some games working and personalized it to my liking, but because I cant leave well enough alone i broke it, some how.  Re-installed and now my sound doesn't work. 

I've used the live disk for PCLinuxOS, Gos, Puppy, and a couple others, sound always works.  Xubuntu, Kubuntu and Ubuntu and my sound doesn't work even with live CD.

I have searched the web (this forum) and havent found an answer.  Can someone walk me through fixing this.  Remember I'm very new to this and dont know alot about command line.

I'm using Nvidia CK804 onboard sound.

Thanks in advance
TJ

---

### Post by VMC on 2008-07-04
> **tj.brewster said:**
> HI been a linux use for about three weeks now.  Installed Ubuntu first, everything worked out of the bok.  Got some games working and personalized it to my liking, but because I cant leave well enough alone i broke it, some how.  Re-installed and now my sound doesn't work. 

I've used the live disk for PCLinuxOS, Gos, Puppy, and a couple others, sound always works.  Xubuntu, Kubuntu and Ubuntu and my sound doesn't work even with live CD.

I have searched the web (this forum) and havent found an answer.  Can someone walk me through fixing this.  Remember I'm very new to this and dont know alot about command line.

I'm using Nvidia CK804 onboard sound.

Thanks in advance
TJ
What does "System > Preferences > Sound" reveal? Does the autodetect and test do anything?

---

### Post by nikgare on 2008-07-04
Are the speakers plugged into USB or the audio out jack?
If usb, are they being seen (you can check this by using **lsusb**)

Are the mixer levels right?
Open the volume control gui and make sure that the correct outputs are turned on, and that the sliders are high enough.

In System->Preferences->Sound does playing a test sound work?
If not, you may need to change the output device here.

---

### Post by tj.brewster on 2008-07-04
Autodetect and test do nothing....speakers are plugged into the audio jacks....PClinuxos live disk and Windows xp work fine.  ALSA mixer looks OK...not muted.  No version of *buntu has sound.

---

### Post by nikgare on 2008-07-04
Don't let ubuntu autodetect - select one of the other options in the Sound playback drop down.

---

### Post by tj.brewster on 2008-07-06
Tried that no difference....anything else I can try short of reformat?

---

