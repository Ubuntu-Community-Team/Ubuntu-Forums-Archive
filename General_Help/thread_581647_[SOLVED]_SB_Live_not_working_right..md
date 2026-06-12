---
title: "[SOLVED] SB Live not working right."
date: 2007-10-19
forum: General Help
---

### Post by NoSmokingBandit on 2007-10-19
I have a fresh install of ubuntu Gusty, which has been fairly impressive so far, but i cant get amarok to play through my sound card. If i go to system>preferences>sound i can hear the test on the 'ADC Capture/Standard Playback PCM' and 'Mutichannel Playback' settings only. I set it to ADC and made sure the volume control in the panel was set to my SB Live card, but i still get no sound.

---

### Post by ZeBadger on 2007-10-19
I've had this problem.  I've done two things.

1) Double clicked the sound icon on the top right to bring up the Volume Control and gone to  File-> Change Device -> selected "SB Live".

2) On the same application underneath "Master" there is a box that had a red X on it.  I unchecked it.  Why oh why?!

Working now!

---

### Post by SveinT on 2007-10-19
I didn't really understand what the problem was exactly, but just in case this could help: SBLive is set to digital output only mode upon installation (you can change it in volume settings).  Dunno if you already knew this or perhaps you're using digital output.

---

### Post by NoSmokingBandit on 2007-10-19
> **ZeBadger said:**
> I've had this problem.  I've done two things.

1) Double clicked the sound icon on the top right to bring up the Volume Control and gone to  File-> Change Device -> selected "SB Live".

2) On the same application underneath "Master" there is a box that had a red X on it.  I unchecked it.  Why oh why?!

Working now!
First thing i did was uncheck every volume slider and turn them all the way up, but that didnt help at all.


> **SveinT said:**
> I didn't really understand what the problem was exactly, but just in case this could help: SBLive is set to digital output only mode upon installation (you can change it in volume settings).  Dunno if you already knew this or perhaps you're using digital output.
Im not using digital output, but im not sure i know how to change the setting in the volume control. I looked all around but didnt see an option for that.

---

### Post by NoSmokingBandit on 2007-10-21
I reinstalled 7.10 since alot of crap was going wrong, now my sound card works. Must have had a bum installation.

---

### Post by NoSmokingBandit on 2007-10-21
Crap! I dont know how to (or if its possible) to unmark this as solved. My sound worked until i installed Amarok, then it stopped functioning. I did notice, however, that in the Volume Control window it moved my sbLive card from the _0_: slot to the _1_: slot. I selected the SBLive card, but still no sound.

---

