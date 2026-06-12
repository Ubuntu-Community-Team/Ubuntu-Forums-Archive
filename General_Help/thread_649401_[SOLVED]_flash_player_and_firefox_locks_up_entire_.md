---
title: "[SOLVED] flash player and firefox locks up entire system"
date: 2007-12-24
forum: General Help
---

### Post by skat3h3ll on 2007-12-24
I know this has been posted many times, but i think my problem is a little bit different

usualy i see people posting saying firefox is the only thing crashing with flash player. 
the problem i am having is not only does firefox crash but the sound hangs and every thing seems unresponsive and i am forced to push the reset button nothing will work no alt+f1 no ctrl+alt+backspace nothing its a total system lockup,

this usualy takes place when i am on youtube since that is the site i use most that uses flash player. 

I am running ubuntu gutsy gibbon 7.10 with the latest flash player installed downloaded from adobe.com and whatever the latest firefox version is :P 

I am sorry if this has been posted and answered before if it has just please direct me to that page :D 

i am not a complete linux noob but i am still new at this so please try to explain with a little more detail when u help me with my issue. i will be very thankful to whomever can help me, this issue has been bugging the crap out of me because i am really starting to love using ubuntu and i frequently go to youtube

---

### Post by Casual Fan on 2007-12-24
Have you tried going to YouTube using Epiphany, Opera, or Swiftfox? All are available in the repositories. If you don't lock up using those browsers, then it's a Firefox problem. If it does, then it's probably a Flash problem.

You may also want to uninstall Flash and/or Firefox via Applications>Add/Remove or Synaptic and then reinstall via Add/Remove, so that you get the versions of Flash and Firefox from the repos, which may be more likely to work together.

---

### Post by skat3h3ll on 2007-12-24
i already had epiphany installed so i went ahead and tried your idea and used that to go to youtube and experienced the exact same problem. its pretty odd because ive been reading other posts about just firefox crashing from flash and people say its usually when they click back or click something. my problem is it happens when im just in the middle of watching a video the whole computer will just lock up and the sound hangs. 

so should i go ahead and uninstall firefox and flash players and reinstall them anyway? 
or do you have any other ideas i might try first ?

---

### Post by skat3h3ll on 2007-12-24
> **skat3h3ll said:**
> i already had epiphany installed so i went ahead and tried your idea and used that to go to youtube and experienced the exact same problem. its pretty odd because ive been reading other posts about just firefox crashing from flash and people say its usually when they click back or click something. my problem is it happens when im just in the middle of watching a video the whole computer will just lock up and the sound hangs. 

so should i go ahead and uninstall firefox and flash players and reinstall them anyway? 
or do you have any other ideas i might try first ?


i just tried with galeon web browser it doesent seem to lock the entire system but it does crash .. hmn im puzzled :confused:

---

### Post by Casual Fan on 2007-12-24
I'd totally remove flash and reinstall it from the repos at this point.

---

### Post by skat3h3ll on 2007-12-25
i just removed a couple packages relating to flash except this ubuntu-restricted extras package. now everything works fine. no more lock ups. i think the issue i was having is i had 2 different flash packages installed,. and they were somehow conflicting. does that sound right? 

anyway thanks for your help and ideas

---

### Post by pissedoffdude on 2007-12-25
When watching a video in flash right click and go to settings then disable video acceleration.  Also check that your default depth is at 24 and not 16 in your xorg.conf.  To check what your default depth is try```
cat /etc/X11/xorg.conf
```

---

### Post by skat3h3ll on 2007-12-25
> **pissedoffdude said:**
> When watching a video in flash right click and go to settings then disable video acceleration.  Also check that your default depth is at 24 and not 16 in your xorg.conf.  To check what your default depth is try```
cat /etc/X11/xorg.conf
```

hmn  not sure if i needed to do that but i went ahead and did it anyway my default depth was already at 24 and i turned off the acceleration

---

