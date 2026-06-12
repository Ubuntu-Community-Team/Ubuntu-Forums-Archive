---
title: "Laptop - No right click menu after upgade to 14.10 from 14.04"
date: 2014-12-05
forum: General Help
---

### Post by musicboy on 2014-12-05
tried everything I can, googled it, read about similar, was one question posted on ask ubuntu, no replies, same problem. Only the menu button on the laptop now works. 

I can get a right click menu but NOT with the right click button I have to place my finger on the touchpad press the left click menu then move the cursor away from the file. this does not work with just on the desktop and creates the first in the menu which is folder so it creates a folder and it does not work on the folders either.

I would appreciate it if someone could tell me how to reset this in nautilus or similar.

Thanks

:guitar:

---

### Post by musicboy on 2014-12-06
Right there is NO fix for this its been logged as a bug and it even effects the live DVD as I tested that then just re installed 14.04. 14.10 is BROKEN PRETTY BADLY for laptop users!! Mainly effectig Acer users and that's the NEWEST acers as well and that is NOOOOOOOOOOOT good AT ALL as Acers are one of the most POPULAR lap tops around!!

That NEEDS fixing before I install a further version of ubuntu for my lap top, Mint is going to have to get installed OTHERWISE and Ubuntu will start to loose me!! IT WHEN they decided to hard code the close, minimise, maximise buttons to the left as well and NOT allow people to CHOOSE........... let people choose for f'sakes!! 

Thread closed

---

### Post by musicboy on 2014-12-06
Marked as unsolvable, Ubuntu 14.10 broken for MANY Acer laptop users!!

---

### Post by musicboy on 2015-04-11
If anyone has this problem, this 100% fixes this issue, why oh why have Canonical NOT included these 2 lines of code as an update?!!

[http://askubuntu.com/questions/579645/right-click-on-synaptic-touchpad-not-working-on-ubuntu-14-10](http://askubuntu.com/questions/579645/right-click-on-synaptic-touchpad-not-working-on-ubuntu-14-10)

sudo nano /usr/share/X11/xorg.conf.d/50-synaptics.conf


Locate the paragraph:


# This option enables the bottom right corner to be a right button on clickpads
# and the right and middle top areas to be right / middle buttons on clickpads
# with a top button area.
# This option is only interpreted by clickpads.
  Section "InputClass"
     Identifier "Default clickpad buttons"
     MatchDriver "synaptics"
     Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
     Option "SecondarySoftButtonAreas" "58% 0 0 15% 42% 58% 0 15%"
   EndSection

Add two extra lines before Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0" :


     Option "ClickPad"         "true"
     Option "EmulateMidButtonTime" "0"


------------------------------------------------------------------------------------------------

Well that will fix it. But why hasn't Canonical worked out this and put the 2 lines of code in I will never actually understand............

it is a bug, that needs to be put right asap.

---

