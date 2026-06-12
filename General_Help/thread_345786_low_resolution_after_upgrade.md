---
title: "low resolution after upgrade"
date: 2007-01-24
forum: General Help
---

### Post by jesuisbenjamin on 2007-01-24
Today i installed Ubuntu and enjoyed a high resolution. Later it offered a set of upgrade and when these were installed, i could not get any higher resolution than 640x480.
What to do??:(

---

### Post by Happy_Man on 2007-01-24
Have you tried 

```
sudo dpkg-reconfigure xserver-xorg
```
?

That usually solves these problems...

---

### Post by jesuisbenjamin on 2007-01-25
Thanks,

This is new to me, how do i use this code?

---

### Post by frolle on 2007-01-25
> **jesuisbenjamin said:**
> Thanks,

This is new to me, how do i use this code?

Open a terminal and then write dpkg-reconfigure xserver-xorg

Its easy as that.

---

### Post by jesuisbenjamin on 2007-01-25
Hey thanks,

i did that and configured x-server, then booted. 
It wouldn't work properly when starting up and eventually i reinstalled Ubuntu.
Now the system is prompting me for updates but i don't dare installing any until i can figure out how to prevent a low resolution issue again.

How can i figure out what happened? What may have gone wrong in the configuration of x-server?

I have an onboard vga controller (compaq) and selected "vga" driver, for the rest i didn't change anything...


thanks

---

### Post by Wim Sturkenboom on 2007-01-25
What is high resolution?

You might want to try vesa instead of vga.

---

### Post by jesuisbenjamin on 2007-01-25
Mmh, i am not sure if you meant "what is a high resolution?" ironically or not, anyways i have now 1024x768 whereas i will have  640x480 after running the updates.
What is VESA? Can i be sure of the result? DO i need to change anything else in *sudo dpkg-reconfigure xserver-xorg*?
It is now configured with VESA by the way and if i recall it was then when i ran it with 640x480 after update issue.

---

### Post by Wim Sturkenboom on 2007-01-26
It's impossible to know if you can be sure that you can restore to 1024x768after the update as it's unknown what went wrong.

The updates might have changed your /etc/X11/xorg.conf which caused your problem.

I suggest that you make a backup of your /etc/X11/xorg.conf and run the updates. After the updates, copy the backup back and try.

If restoring does not work, it's a pitty and you might have to start all over again (not nice to hear).

---

### Post by jesuisbenjamin on 2007-01-27
Ok i get it, so i went to etc/x11/xorg.conf and printed it out. I imagine  can try to run my updates and then compare the results on the new configuration of Xorg and make sure they are set as they were beforehand?
Would that be a good strategy?

Thanks for your help.

---

### Post by Wim Sturkenboom on 2007-01-28
It's always a good idea to compare; it might give some understanding.

I still would make the backup as well. That way you can use *diff* to compare. And you can always copy the backup back in case of 'emergency'.

Good luck

---

