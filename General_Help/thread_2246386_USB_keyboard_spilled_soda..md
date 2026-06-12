---
title: "USB keyboard spilled soda."
date: 2014-09-30
forum: General Help
---

### Post by Vindows Wista on 2014-09-30
I used a USB keyboard and accidentally spilled soda on it. Now I can't use my laptop key board. The A and B keys don't work. I have 14.04 and 13.10 installed along with vista....(ironic) I know... I just need the a and b keys back. They are apart of my PW....the A and B keys won't work in the bios as well..I tried.

---

### Post by Elfy on 2014-09-30
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Vindows Wista on 2014-09-30
I appreciate your response Elfy, but I don't need to reset my password. My laptop keys aren't working as they should be.

---

### Post by deadflowr on 2014-09-30
Aside from holding out hope that the keys will dry up enough to function again, which is probably a long shot. Ubuntu's login screen has the ability to use an on-screen keyboard which you can use the mouse for. It should be up top in the panel on the right side.

I know this, because I have a keyboardless machine right now, and the only way to use it is on-board.
(Luckily not this one)
Ain't a fix, but is a very slow work around.

---

### Post by Elfy on 2014-09-30
get a new keyboard, clean the keyboard, keep drinks away from the keyboard if you're apt to spill them or reset the password - not sure what you expect people to do about your physical hardware issues to be honest ;)

---

### Post by tgalati4 on 2014-09-30
Soda is bad for you.  Is it possible that soda splashed on the laptop keyboard as well?  It's hard to imagine how a failed USB keyboard can affect an internal laptop keyboard, unless the 5VDC USB power supply has been damaged.  Do other USB devices (like flash drives) work on all USB ports?

Look for errors.  Open a terminal:

```
more /var/log/Xorg.0.log
```

---

### Post by oldfred on 2014-09-30
If keyboard shorted out, it is gone. 

Some say yes and others say no to cleaning in dishwasher:

Use dishwasher
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Do not use dishwasher
[http://www.daskeyboard.com/blog/how-to-clean-your-keyboard-dont-use-the-dishwasher/](http://www.daskeyboard.com/blog/how-to-clean-your-keyboard-dont-use-the-dishwasher/)

but if you attempt to use dishwasher, you must thoroughly dry it and do not use any ovens or methods to speed up the process. Takes days to dry, so you probably want a new keyboard anyway.

---

### Post by Vindows Wista on 2014-10-01
Thanks for the replies but the soda spilled on the USB keyboard not the laptop keyboard. It was three feet away and I'm sure it did not get wet from the soda. I made sure that caps lock and num lock were off before unplugging the USB keyboard. I'm just unsure why the A and B keys aren't working.

---

### Post by deadflowr on 2014-10-01
Even though the keys are apart the layout of the electronic pathways(?) are probably right next to each other, which probably where the short is, I would assume.

---

### Post by Vindows Wista on 2014-10-02
Ill just try to replace either or... I'm just amazed that the laptop keyboard would give out as soon as the USB keyboard did. Especially since the USB keyboard gave up because of a accidental spill.

---

### Post by tgalati4 on 2014-10-02
From Post #6:  Do all of your USB ports work with other devices?  If the keyboard shorted and that damaged the USB power supply on the laptop, then that could affect the internal keyboard if it uses the same USB bus.  Do you drink regular Coke or Diet?

---

