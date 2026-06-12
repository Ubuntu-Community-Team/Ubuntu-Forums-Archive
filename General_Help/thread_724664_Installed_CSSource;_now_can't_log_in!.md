---
title: "Installed CS:Source; now can't log in!"
date: 2008-03-14
forum: General Help
---

### Post by spadewarrior on 2008-03-14
Hello,

I have just rebooted after running Counter Strike: Source in the latest version of Wine for the first time (which worked flawlessly) and now my log on screen is out of range for my monitor. I can hear the 'bongo' log on sound but can't see the screen. Everything up until that point is normal boot wise. Or at least it seems that way to me.

I'm typing this from a Damn Small Linux live CD as I can't log in from recovery mode either (it hangs when it fails to load Firestarter).

I don't understand how this could have happened as I haven't edited my xorg.conf. The only thing I can think of is that previous attempts to run CS:S were with older versions of Wine which crashed to a lower resolution (800x600) than normal. i always just changed back to my normal resolution after this so don't understand how my settings could have become warped.

Please help me, I'm quite worried that I've done something very, very bad! I can get to a terminal prompt by interrupting the recovery mode start up with ctrl-c (I think) but startx fails and I have no networking capabilities. I'm at a bit of a loss. And I'm a total noob.

Please help ASAP!

:(

---

### Post by spadewarrior on 2008-03-15
Bump.

Any suggestions?

---

### Post by cherva on 2008-03-15
Can't you login in a virtual console ( Ctrl + Alt + F1 ) when you hear the login sound and check your xorg.conf file ?
Or type ```
 sudo dpkg-reconfigure -phigh xserver-xorg 
``` to automatically update your xorg.conf

---

### Post by spadewarrior on 2008-03-15
I'll give that a try and post back. Thanks.

---

### Post by spadewarrior on 2008-03-15
Unfortunately Ctrl + Alt + F1 just gives me a black screen. It's in range for the monitor though, which is a start.

Is there anything else I can try?

---

### Post by louieb on 2008-03-15
> I can get to a terminal prompt by interrupting the recovery mode start up with ctrl-c (I think) but startx failsThat is what Ctrl+Alt+F1 should do. Try  the suggestion ***cherva ***gave, then reboot  and see what happens.
If you have a problem the try it without the **-phigh** option.

---

### Post by spadewarrior on 2008-03-15
Right, I booted back into recovery mode and tried Ctrl + Alt + F1 but that didn't work, so I did Ctrl + C and entered the above code. This seems to have fixed my x server resolution.

Is there anyway that I can stop this from happening again? I'm not sure what I did to mess it up.

edit: Right, it seems to do this every time I run Counter Strike:Source. I guess that's messing something up. Thanks guys.

---

### Post by cherva on 2008-03-15
Why don't you start CSS then when this happenes copy the xorg.conf lile ```
sudo cp xorg.conf xorg.conf.MESSED
```
then fix your xorg.conf anain and post the messed file and the fixed one to see what exactly is wrong with it....
P.S I play CSS v33 with wine every day and I don't have problems with it .....
Do you run CSS as root  ?

---

### Post by spadewarrior on 2008-03-16
Good suggestion, I'll do that.

I don't run it as root, no.

---

