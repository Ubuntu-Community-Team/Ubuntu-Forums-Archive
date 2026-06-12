---
title: "Curious Reboot Problem"
date: 2015-06-09
forum: General Help
---

### Post by albogdan on 2015-06-09
Hello, 

This is my first time posting on this forum because I'm still a new Linux convert :D, I would just like to point out that I am enjoying this OS far more than expected. 

MY system has been running smoothly other than a few problems here and there that google has easily provided answers for. 

The only problem i cant seem to figure out is when i restart my computer. Upon restarting my computer it goes to a black screen and will just sit there indefinitely. Only once ive restarted it again, so twice in a row, it will successfully boot up asking me if i want to start up ubuntu normally or in safe mode etc and i choose to start up normally and then everything runs as it should. This problem happens EVERY time i boot my computer and will only properly reboot upond the second time i boot my computer. 

Is anyone familliar with this problem and could potentially help me out?

Im not entirely sure what I'm supposed to add for extra details but I was previously on windows 7, my computer is a notebook HP, im using ubuntu, and it was a full system overhaul so no dual boot on my system, ubuntu only. 

Thanks! :)

---

### Post by Bucky Ball on 2015-06-09
Welcome. It may not have a lot to do with it, but which release/flavour are you using? A straight Ubuntu install? Which release (what's the number)?

What model of HP is it? Should be on the bottom of the machine. Is that old? How much RAM, if you know?

---

### Post by albogdan on 2015-06-09
Thanks! 

Okay Im using Ubuntu 14.04 LTS, 
the HP is Pavillion dm3-1020ca entertainment notebook PC
I've got 3.6 GiB of RAM
and i think the computer is at least 6 years old,
[h=2][/h]

---

### Post by Bucky Ball on 2015-06-09
Thanks. When it goes to the black screen on boot, can you hold down control+alt then hit F1. Does that take you to a giant terminal? If so, issue:

```
dmesg
```

Can you spot any anomalies at the bottom of that output?

Are you getting to the list of bootable kernels (the grub selection screen), choosing to boot one then the machine is 'blacking' instead of booting to the OS? If you can get to that selection screen, choose the 'Recovery' kernel, which should be second on the list, and keep an eye on the read out to see if you spot anything. When you get to the options, choose 'Drop to terminal as root' (something like that) and type:

```
dmesg
```

See if you can find some errors at the end of the output.

---

### Post by albogdan on 2015-06-09
Hmm so i tried doing doing the ctr + alt + f1 when i restart it and I can't get it to work.
And yes im getting the grub selection screen but only when i restart it for the second time. 
So once i get to the grub screen it will restart normally but if i restart it just once all i get is black screen with a white dash in the upper corner and doesn't let me type anything. 

I'd also like to add that when i do finally get it all booted back up again sometimes it tells me to send my error report which hasn't appeared the last few times but it seems to mention something about:

check.resume

I wish i had more to say. Maybe i can try and get the error report to pop up again.

*edit*
I forgot to mention that there was a prompt to hit " c " in the grub selection menu for some kind of terminal
I tried it out and typed ' dmesg ' but it had no effect.

---

### Post by Bucky Ball on 2015-06-09
We need to see the contents of that error report. You should be able to click the 'Details' in the bottom left, copy/paste what it says in more detail here. :)

---

### Post by NoWayWin8 on 2015-06-09
> **albogdan said:**
>  I forgot to mention that there was a prompt to hit " c " in the grub selection menu for some kind of terminal I tried it out and typed ' dmesg ' but it had no effect.  The 'c' is a shortcut to the grub **c**ommand-line. This interupt the boot and leaves you with a mysterious **grub>** prompt on a black screen. When confronted with this, type the word **normal** and hit enter to return to the grub menu which should automatically boot after a 10 second countdown.  Also you say the error mentions something about "resume" - I would take that to mean the error is related to resume from hibernation/suspend to disk. Maybe removing hibernate/suspend options in Power settings will fix it?

---

### Post by Bucky Ball on 2015-06-09
Yes, that's a point. Are you installed in EFI mode or legacy? Have a look in the BIOS and check that fast start, or something like it, is not checked. Don't know if it's actually used on a solo Ubuntu install, though. Thought it was a Win thing.

---

### Post by albogdan on 2015-06-11
Alright so in my BIOS the only thing that looked like what you were saying was BIOS version? Maybe i wasn&#8217;t looking at the right thing but my BIOS version was F.09

I did turn off 'suspend when lid closing' and tried that out as well i noticed that when i turn my computer back on and it gives me the black screen that leads no where, if i press the f1 key it switches back to the purple ubuntu screen where i can log in again which turns out to be a temporary solution to my problem. 

So in the case where i shut it off and restart it the first time and it sends me to the black screen, by pressing f1 i can successfully log in from there. 
I noticed when i press the f3 key it goes back to black screen and with f1 and f3 I can jump back and forth.

The interesting thing is when i do this on a second start up (one that starts up normally) the blacks screen i get from hitting f3 so purple to black screen gives me a pulsing dashed line as if a terminal, but when the black screen happens on the first start up (the one that normally wont work) i get no dashed line but can still return the to the normal unlock disk purple ubuntu screen. 

Also no luck on getting an error report again.

Any thoughts on this? I suppose my problem is solved although not ideal, it will work for now :)

Thanks for helping me out btw!

---

### Post by Bucky Ball on 2015-06-12
Try ctl+alt+F7. That is where the desktop lives. You say you hit F1. I presume you mean ctl+alt+F1? If you're just hitting F1, does any key on the keyboard bring back the login screen? If this is so, then that is normal for a locked screen after suspend.

---

