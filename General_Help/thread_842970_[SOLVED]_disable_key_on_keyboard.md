---
title: "[SOLVED] disable key on keyboard"
date: 2008-06-27
forum: General Help
---

### Post by Deutscher Alex on 2008-06-27
My keyboard has an incredibly dumbly placed "sleep mode" key that I occasionally accidentally hit.

Is there any way that I could disable that one key?

---

### Post by sdennie on 2008-06-27
Is it a desktop machine?  If so and, you never use the "sleep" mode, you could probably disable it by hitting Alt-F2 and typing gconf-editor.  Then navigate to /apps/gnome-power-manager/general and uncheck can_suspend and can_hibernate.

---

### Post by drs305 on 2008-06-27
This works for symbols. Since it is merely sending a signal, I would expect it to work for this situation as well.

Run the following command to find the keycode value of the desired key:
```
xev
```

With the small box in foreground, press the sleep key and note the keycode value.
Then run this:
```
 xmodmap -e 'keycode **number** = NoSymbol'
```

That should disable the key. To make it permanent, put this command in the System, Preferences, Sessions, Startup Programs folder, Add.

Edit: Typo corrected. Thanks *Sepero*.

---

### Post by Deutscher Alex on 2008-06-27
> **vor said:**
> Is it a desktop machine?  If so and, you never use the "sleep" mode, you could probably disable it by hitting Alt-F2 and typing gconf-editor.  Then navigate to /apps/gnome-power-manager/general and uncheck can_suspend and can_hibernate.
Thanks! Worked very nicely. When I press the key, however, it comes up with a hundred popups saying "action disallowed", lagging my system to death for about a minute. Is there any way I can disable that too?

EDIT: problem solved; I changed the value of suspend in Gnome-Power-Manager > Buttons to "nothing"


> **drs305 said:**
> This works for symbols. Since it is merely sending a signal, I would expect it to work for this situation as well.

Run the following command to find the keycode value of the desired key:
```
xev
```

With the small box in foreground, press the sleep key and note the keycode value.
Then run this:
```
 xmodmap -e '**keycodenumber** = NoSymbol'
```

That should disable the key. To make it permanent, put this command in the System, Preferences, Sessions, Startup Programs folder, Add.

Thank you; this is a very useful tool. I have to go with vor's way though, because my computer can't recover from sleep mode, and therefore I can't note the keycodenumber >.<; And that way also prevents me from making it go into sleep/hibernate from the shutdown window.

---

### Post by sdennie on 2008-06-27
> **Deutscher Alex said:**
> Thanks! Worked very nicely. When I press the key, however, it comes up with a hundred popups saying "action disallowed", lagging my system to death for about a minute. Is there any way I can disable that too?

EDIT: problem solved; I changed the value of suspend in Gnome-Power-Manager > Buttons to "nothing"


Glad it worked.  It probably would have been sufficient to make that change in the first place but, I'd forgotten that option was there.  ;)

---

### Post by Deutscher Alex on 2008-06-27
> **vor said:**
> Glad it worked.  It probably would have been sufficient to make that change in the first place but, I'd forgotten that option was there.  ;)

Hmm yea, but now I don't have those extraneous suspend/hibernate options on the shutdown screen =)

---

### Post by drs305 on 2008-06-27
vor's method would certainly be the way to go in that it directly addresses the power mode instead of indirectly altering a key. 

for future reference or other readers, there is an alternate method of discovering the keycode in cases such as this one where you might not want to actually press the key (d'oh!). you can run this and then find the keycode. for normal keys you could limit the output by adding " | grep *symbol* "  but in this case the sleep key isn't called sleep, at least on my computer.
```
xmodmap -pke
```

glad you were able to solve your problem :)

---

### Post by webbsd on 2010-03-21
Cheers drs305. I used this successfully to disable the MS Windows Menu key:

xmodmap -e "keysym Menu = NoSymbol"

Steve.

---

### Post by Sepero on 2010-06-16
> **drs305 said:**
> This works for symbols. Since it is merely sending a signal, I would expect it to work for this situation as well.

Run the following command to find the keycode value of the desired key:
```
xev
```

With the small box in foreground, press the sleep key and note the keycode value.
Then run this:
```
 xmodmap -e '**keycodenumber** = NoSymbol'
```

That should disable the key. To make it permanent, put this command in the System, Preferences, Sessions, Startup Programs folder, Add.


The command should be:
xmodmap -e 'keycode **number** = NoSymbol'

---

### Post by brain!ac on 2010-07-15
Sory to reply on a Solved thread but i have a question ,does it work only on X.Session because i wan't to disable a key at GRUB Boot Loader menu ?

Is that possible to block it through this tool ?

---

### Post by Sepero on 2010-07-15
Only works with Xwindows. sorry

---

### Post by brain!ac on 2010-07-16
> **Sepero said:**
> Only works with Xwindows. sorry

thanks :-({|=

---

### Post by jobsworth on 2011-09-28
Thank you for this very helpful thread.
I diagnosed that my laptop had dirt or condensation under the right shift key.
So I wanted to disable this key. It was permanently ON.

xmodmap -e 'keycode 0x3e = NoSymbol'

did it for me.

The difficult part was to type xev.
The solution was to use caps lock so that XEV became xev.

That did not solve the problem of how to type - which was _
nor numbers, 1234 was !@#$.
Worse than that the right shift was intermittent like inTermIttent.
The solution was to create a text file on another machine
containing xmodmap -e 'keycode 0x3e = NoSymbol', copy it to a USB stick
and then transfer the file to the laptop.
Then copy and paste the string to a terminal window.

I may yet have to buy a new laptop keyboard.

---

