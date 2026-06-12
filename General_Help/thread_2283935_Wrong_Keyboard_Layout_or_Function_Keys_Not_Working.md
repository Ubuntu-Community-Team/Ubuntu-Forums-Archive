---
title: "Wrong Keyboard Layout or Function Keys Not Working (mutually exclusive issues)"
date: 2015-06-25
forum: General Help
---

### Post by brad40 on 2015-06-25
Hey guys, I recently installed Xubuntu on my laptop and I've ran into a rather odd issue. As a precursor - my keyboard layout is set to English (UK) in keyboard settings.

Essentially, these two issues are mutually exclusive, only one happens at a time. The issues are listed below:

1. My keyboard is in the wrong layout. I use the GB layout for my keyboard but it uses the US layout in reality (e.g. " where @ is supposed to be). This can be easily fixed by using Dconf editor to modify the value of the use-system-keyboard-layout checkbox (the issue gets completely resolved after a restart and the keyboard continues to work fine, in the GB layout). However, when this fix is applied and the computer is restarted, the next issue occurs.

2. None of my function keys work (e.g f2 and f3 for my brightness controls, f9 and f10 for my volume controls). These work when the previous checkbox isn't ticked.

I've been loving the Ubuntu experience thus far, but these two issues are making it incredibly difficult to use my laptop the way I intend to use it. Any possible solutions would be a godsend, thanks in advance guys!

---

### Post by gdesilva on 2015-06-25
@brad40, I did have a similar problem to yours with function keys - none would work. Then when I had closer look I found that there is a 'FLock' key ( in my case after F12) which toggles function keys on and off. So, it may be worth checking whether your keyboard has a FLock key as well.

---

### Post by brad40 on 2015-06-26
> **gdesilva said:**
> @brad40, I did have a similar problem to yours with function keys - none would work. Then when I had closer look I found that there is a 'FLock' key ( in my case after F12) which toggles function keys on and off. So, it may be worth checking whether your keyboard has a FLock key as well.

Hey, cheers for the response. Sadly, this isn't the case with my laptop, oh how I wish it was. It seems very temperamental in terms of whether the function keys actually work now, it doesn't seem like the issues are mutually exclusive after all. The keys which are affected by this do not register as being pressed on the test keyboard in keyboard settings, just a little info to update things I guess!

---

### Post by gdesilva on 2015-06-26
Have you tried using xev? This will tell you what key code is generated when pressing a key. If no output or incorrect output then obviously you have a hardware problem - probably worn out circuit (paint) on your keyboard due to a liquid spill. I have a keyboard damaged by spilled Coke on it. I cleaned it and got it to work except for the X key and found out that the contact paint used for the circuitry was damaged.

---

### Post by brad40 on 2015-06-27
> **gdesilva said:**
> Have you tried using xev? This will tell you what key code is generated when pressing a key. If no output or incorrect output then obviously you have a hardware problem - probably worn out circuit (paint) on your keyboard due to a liquid spill. I have a keyboard damaged by spilled Coke on it. I cleaned it and got it to work except for the X key and found out that the contact paint used for the circuitry was damaged.Hey, this definitely isn't the issue as I currently dual boot Windows 7 and all keys work as they should. :)

---

### Post by Bashing-om on 2015-06-27
brad40; Hello;

Maybe try the simple things 1st prior to advancing to the more complex:
> 
For the record, In 14.04 we now have something that we never had in 12.04. A keyboard app indicator icon in the top panel. Click on that and select Text Entry Settings and we get the dialog to add or remove keyboard layouts. We can also go to System Settings>Keyboard and at the bottom left of the dialog are the words "Text Entry." Click and we get the same add/remove keyboard layouts dialog. (Graham)


[INDENT][INDENT]keep'n to as simple as possible
[/INDENT][/INDENT]

---

