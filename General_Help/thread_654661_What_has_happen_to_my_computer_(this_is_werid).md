---
title: "What has happen to my computer (this is werid)"
date: 2007-12-31
forum: General Help
---

### Post by dellboy on 2007-12-31
ok right i right i login my computer in to windows for the first time in a few weaks. as i need to do somthing in windows that i could not in ubuntu. after i do it i want and longed  back in to you ubuntu to find that my screen is all messed   and very big. i nomaly  use 1204x786  but i can not longer seen this when i go in to ubuntu to change it to make it not so big.

What i want to now what has windows done to my computer i think before the windows xp login screen my mounter sayed fixing screen to fit or something like that.

Help what has happen to my computer

---

### Post by taurus on 2007-12-31
Just reconfigure your screen again.

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, restart X server with <Ctrl><Alt>Backspace.

---

### Post by dellboy on 2007-12-31
ok great that did it.

ps how did it work.

i now have a problem with amsn it only seems to be with that program 

i can see what i tipy but i can not see what people tipy to me. i unstilted and reinstalled did not help me.
pidgin it works on 

and how did this happen to my computer was it windows that done it did you ubuntu do it 

ps i like to fix the amsn thing as i like that as an IM client

thank you for your help  taurus

---

