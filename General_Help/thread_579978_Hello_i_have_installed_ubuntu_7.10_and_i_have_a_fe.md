---
title: "Hello i have installed ubuntu 7.10 and i have a few problems?"
date: 2007-10-18
forum: General Help
---

### Post by origr15 on 2007-10-18
1.when i installed gusty gibbon i had 3d effects and then a restricted drivers window poped up and told me that they can install ati driver ' and i agrees and now i dont have 3d only normal.
2.when i press the mute button on my keyboard it shows that it mutes but it really doesn't.
3.when i press the lower volume and rise volume it doesnt work but it shows me it tried to do it.
please help me!:popcorn:

---

### Post by arjones85 on 2007-10-18
> **origr15 said:**
> 1.when i installed gusty gibbon i had 3d effects and then a restricted drivers window poped up and told me that they can install ati driver ' and i agrees and now i dont have 3d only normal.
2.when i press the mute button on my keyboard it shows that it mutes but it really doesn't.
3.when i press the lower volume and rise volume it doesnt work but it shows me it tried to do it.
please help me!:popcorn:



Try following the documentation regarding compiz and ati cards:
[https://help.ubuntu.com/community/CompositeManager/CompizFusionATI?highlight=%28compiz%29](https://help.ubuntu.com/community/CompositeManager/CompizFusionATI?highlight=%28compiz%29)

And more specifically:

Install XGL

      sudo apt-get install xserver-xgl

---

### Post by AnthoMacP on 2007-10-18
If you have speakers plugged in through a headphone jack then it won't mute them properly because it assumes you have headphones plugged in and not a real set of speakers. If you're using a desktop plug the speakers into your real audio jacks (ie. not the ones with the lil pic of a headphone). If you're using a laptop you'll just have to unplug the speakers from the plug every time you mute unless you manually go into your audio settings and drag the headphone bars down. I'm sure there's probably a way for you to change what is actually muted but i'm assuming that's what the problem is, same goes for the audio up and down. That's how it works on my system anyway

---

### Post by origr15 on 2007-10-19
i have normal speakers,i also have a windows on this pc and it works for it!

---

### Post by xarmian on 2007-10-19
> **origr15 said:**
> i have normal speakers,i also have a windows on this pc and it works for it!

Try the following:

1. Go to System->Preferences->Sounds, go to the bottom window

2. Select PCM and then close.

3. Right click the speaker icon and select "Open Volume Control" and drag PCM to the bottom, Master to the top, and Headphone to the top

4.  To avoid a future headache, click the "Switches" tab and select "Headphone Jack Sense"

5. Try using your keyboard volume control now.  Some or all of the buttons may still not work, which will require fixing the keybinding.  IF mute or the volume control buttons still do not work:

6. Go to System->Preferences->Keyboard Shortcuts

7. Scroll down to "Volume mute", "Volume down", "Volume up"

8. Click the area under "Shortcut" next to the volume control you want to change, and it will say "Enter accelerator"

9. Press the volume control key on your keyboard, and the "shortcut" area will be filled in with a hex value automatically.  When you're done, click Close.

10.  Now try the volume controls, they should work.

This is written based on Feisty since the repos are overloaded and the upgrade is taking forever, but I'd imagine the procedure didn't change too much with Gutsy.

-Dave

EDIT: Fixed steps 1 and 2.  Made a mistake.  Edit2: Made it more obvious that the second half is only if things aren't working :)

---

### Post by origr15 on 2007-10-19
thanks it worked both sound and and 3d effects :):):)

---

