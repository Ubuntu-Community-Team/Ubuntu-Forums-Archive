---
title: "help with keyboard mappings"
date: 2007-12-14
forum: General Help
---

### Post by bergamot on 2007-12-14
I was wondering if it is possible to make it so that a key on the keyboard can be configured to do a left mouse click.

My laptop touchpad's left button has stopped working, and it's not too keen on the "tap to click" thing either for some reason, so rather than plugging in an external mouse every time, I thought it would be nice if I could use the "windows" key to do the left mouse clicks.

I had a look in the Keyboard Shortcuts application, but Left Mouse Click doesn't seem to be in there. I had a look in xmodmap too, but it's rather daunting and I would need some help from someone experienced in such matters, because I don't really know where to start on that. Or is there a handy application to do the keyboard mapping without editing files manually? (I did a search in Synaptic but didn't find anything appropriate)

Many thanks

---

### Post by frodon on 2007-12-14
Yep  xmodmap is the way to go IMO in your case.

First get the keycode of the key where you want to map your left button, for this open a terminal and type "xev" in, it will open a small apps which will give you a detailed information of each key or button you will press. So once xev opened type the key where you want to map your left button and note the corresponding keycode.
I give you an example of ourput with the "c" letter :
```
KeyRelease event, serial 26, synthetic NO, window 0x4800001,
    root 0x3e, subw 0x0, time 360026161, (170,-17), root:(174,708),
    state 0x10, **[COLOR="Red"]keycode 54[/COLOR]** (keysym 0x63, c), same_screen YES,
    XLookupString gives 1 bytes:  "c"
```

Lets say you map it on letter c so as the output show it the keycode of this key is 54 then the xmodmap and xkbset command to map your left button onthis key will be something like :
```
xmodmap -e "keycode  54 = Pointer_Button1"
xkbset m
```The only thing i am not sure is about the Pointer_Button1 to tell to use left mouse button.

Then once you have the right xmodmap command create a script and add it in your session startup scripts and you are done ;)

---

### Post by bergamot on 2007-12-14
Thanks a lot, that was very useful.
To get it to work, I had to open up the Keyboard Accessibility application in the System -> Preferences, and enable the accessibility features and specifically the MouseKeys. (doing xkbset -m didn't seem to do the trick).
Then I did this:

```
xmodmap -e "keycode 115 = Pointer_Button1"
``` 

...and now my Windows key is the left mouse button! :)

Now, I would like it so it works when I log into my Gnome desktop so I don't have to type the command in every time. In the old days you could put commands in .xinitrc, but this doesn't seem to work anymore. I also tried putting the command in .gnomerc, but again, no joy.
Do you know which configuration file I have to put it in?

Thankyou and much appreciated

---

### Post by frodon on 2007-12-14
Create a script which contain your xmodmap command, make it executable then go in system > preference > session and add a new startup script, fill the command field with the full path of your script.

Glad you got it working, these are things not easy to do when it is the first time you have to map a key.

---

### Post by bergamot on 2007-12-15
Yes that worked fine - thanks again.:cool:

---

