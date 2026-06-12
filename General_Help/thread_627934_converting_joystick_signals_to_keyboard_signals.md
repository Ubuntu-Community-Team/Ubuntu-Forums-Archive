---
title: "converting joystick signals to keyboard signals"
date: 2007-11-30
forum: General Help
---

### Post by nzadLithium on 2007-11-30
Hey

I been wanting to try and play Return To Castle Wolfenstein with a joystick for a while now. (just because im crazy and want to make the game harder for myself). I have my joystick setup its a saitek cyborg evo. It works fine in games like planet penguin racer etc but in older games they only seem to support analogue joysticks im assuming its something to do with the way the device nodes are setup.

I've decided i want to try out the joy2key program. So i installed it from ubuntu repositories its all setup. Took me a while to figure out how to write in what i want each button to do but i kinda figured it out.

At the moment since im just trying it out i havent set up any crazy configs.

I'm using this command to run it: 
sudo joy2key -dev /dev/input/js0 -X -axis Left Right Up Down -buttons Return a
what this is basically doing is telling it my joystick is device (node ?) is at /dev/input/js0 then telling it its supposed to be sending X signals then telling it that axis zero low is left axis 0 high is right etc then telling it button zero is the ENTER key and button one is the a key.
(im assuming the joystick axes and buttons start at 0)

The problem im having is it seems the shift modifier is always applied. Does anyone here know how to get it to stop sending shift???

---

