---
title: "[SOLVED] USB Mouse does not move (Clicks work)"
date: 2007-08-08
forum: General Help
---

### Post by Harika on 2007-08-08
First, I apologize if this is in the wrong forum as it does not seem to be a hardware problem to me. 

I just loaded Ubuntu 7.04 onto my win xp system (dual boot). The live cd went smoothly, like normal. I had several hard-drive errors when installing but installation was successfull.

The mouse DID work in the live cd environment. Once I completed the install I booted up into Ubuntu, I had a couple more hard drive errors but ubuntu was able to correct them. (I am sorry for the lack of specifics about the errors.)

when logged into the fully installed Ubuntu OS (not the live cd) I was unable to use the mouse for movement. I could left click and roght click but nothing I could do would enable movement. 

Several reboots produced the same results with no more HD errors. 

The mouse is a : Microsoft Wheel Mouse Optical USB and PS/2 compabable.

Any sugestions are apreciated. I just started with Ubuntu so I am not an advanced user. I would consider myself an expert on windows as that is my job. 
I would guess (based on my windows knowledge that: 
1:there is a problem with the mouse drivers/software <most likely


Again, sorry, and thank you
Harika

---

### Post by anubhavrocks on 2007-08-08
DId you try connecting the mouse to PS/2 ?Just give it a try if it works.
ALso post the output of 
```
dmesg
```

---

### Post by Harika on 2007-08-08
[INDENT]> "DId you try connecting the mouse to PS/2 ?Just give it a try if it works.
ALso post the output of 

Code:
dmesg"[/INDENT]

Good idea about the PS/2.  

what is dmesg and how can I run it without a mouse? :) (I would guess the terminal but how could I open it?)

-Harika

---

### Post by anubhavrocks on 2007-08-08
press ```
ALT+F2
```  and inside that type ```
gnome-terminal
```

Once you are inside the terminal type ```
dmesg
```.

---

### Post by Harika on 2007-08-08
Thanks, I will try that as soon as I get home.

---

### Post by Harika on 2007-08-08
When I got home the mouse was magicaly working again. I unpluged it a few times, changed it to ps/2 a few times, nothing could replicate my problem. 

Thank you for your time! I really apreciate your willingness to help.

---

