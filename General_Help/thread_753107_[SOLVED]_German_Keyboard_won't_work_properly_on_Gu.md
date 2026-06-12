---
title: "[SOLVED] German Keyboard won't work properly on Gutsy."
date: 2008-04-12
forum: General Help
---

### Post by svaens on 2008-04-12
Hi all, 

I raised this issue via launchpad, but was told it 'won't be fixed'.
Bug number 216338

I am unable to type the @ character whilst using the German keyboard layout. 
I have been told to try using the AltGr key, 
but since I have an american (physical) keyboard, I have no AltGr key. 
This is specific to the physical German keyboards. 
I hoped my right hand side Alt key would do the job, but it just caused my editor to quit. 
Normally, on a german keyboard (and i know several germans, since i am living in germany) use the ctrl-alt (left side) - Q combination to get their @ character. Not the AltGr key anyway. It is easier to do. 

Is anyone else able to type an @ character using the German keyboard layout, having a normal American English keyboard?

I rather think that this problem should be given more consideration.

---

### Post by jakupl on 2008-04-12
As a temporary solution, you can right click on the top panel, press "Add to panel" and insert the "Character Palette".

You can customize witch characters should be there, I personally have "üÜþÞ" as I have ü in my last name and þ as I write Icelantic occationally.

When you press a character on the palette, it automatically goes to the clipboard, so you can paste it in documents.
This will of course be irritating if you use the letters often, but then you can write the letters you want.
If "@" is your only problem, then this is perfect for you.

---

### Post by der_joachim on 2008-04-12
How does the keyboard layout in /etc/X11/xorg.conf look? You may have configured your right alt key as a compose key for instance. I did. Never went back. No experience though with any German layout. 

I did configure it temporarily though and Right-Alt+Q did the trick for me. :-k

---

### Post by svaens on 2008-04-12
ahh damn. 

Or rather, good. 

Damn, because i have shamed myself, basing my discovered 'bug' on incorrect information, and complaining when noone wanted to fix it, 

and

GOOD!! Because there is no bug. 

Turns out the key combination which my german gf told me, while works on microsoft windows, is not the correct key combination. 

AltGr (the right alt key) + Q  

is the correct key combination. 

Which is even better, because not only can I enter the @ symbol now on a german layout, 
I only have to use two keys now, instead of 3. 

Thanks to the guys who replied to this thread for the helpful work arounds, 
and thanks to the patient person who worked this through with me on launchpad.

---

### Post by jakupl on 2008-04-12
I am happy it worked out for you.

Please mark this thread as solved to save time for us all :KS

---

### Post by svaens on 2008-04-12
hmmm....  and for my next question... 

how to mark a thread as solved....

---

