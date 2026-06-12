---
title: "OSD Volume Indicator doesn't actually reflect volume levels?"
date: 2007-03-06
forum: General Help
---

### Post by fictivetoast on 2007-03-06
A strange problem popped up a few days ago, after months of merrily running dapper, then edgy, and now feisty with all updates - I have an hp nc6000 laptop with volume up, volume down, and volume mute media keys.  Ubuntu has always recognized these with no problem, and upon their use has present a handy little OSD indicating the resulting change to the master volume level.

Quite suddenly however, the volumes and indicator seem no longer tied to anything.  The sudden disappearance of function didn't seem to correlate with any updates or other system changes either, at least that I'm aware of.

When I press the "volume mute" button for example, the OSD pops up and shows an image of a muted speeker... but the actual master volume level remains wholly unchanged.  Same goes for volume up and volume down - the OSD claims something is being changed, but NONE of the volume levels in gnome-volume-control are reflecting anything, and the system sound remains the same.

My keyboard shortcuts are properly reflecting the media keys too - so gnome *knows* the volume should be changing, the message just isn't being passed on somewhere along the line.  

Any thoughts?

---

### Post by discovery on 2007-03-07
I am on a Dell Inspiron6000 and am experiencing the same exact situation. Its pretty annoying, especially since the buttons were working earlier today! I will definately keep searching for answers and post anything i find back here. 

Hope someone has more of a clue than me.


EDIT: The buttons are correctly mapped and the OSD volume meter is actually correct when my headphone are not connected. This is why i did not notice this behavior earlier, I did not have my headphones in. Hopefully this helps narrow the problem.

fictivetoast, i wonder if this happens with you as well.

---

### Post by po0f on 2007-03-07
fictivetoast / discovery,

Navigate to System->Preferences->Sound.  In the bottom combo-box, Ctrl-Left Click all the sound "devices" you want controlled by the volume keys.

At least, this works for me.  :)

---

### Post by 4tro on 2007-03-26
i noticed some other odd behaviour in my feisty today.

all of a sudden my MX1000's side-scrollers started to control my volume...
that's a good thing... but in my opinion they should be switched in function...

pressing the sidescroller to the left should decrease volume, to the right increase it.
the way it is set up now is good for left-handed mice though.

anyone has an idea?

---

