---
title: "compiz rotate"
date: 2008-06-19
forum: General Help
---

### Post by hotwater12 on 2008-06-19
Hello,

I have a little problem with my Hardy. I have compiz and I can't rotate the cube with my wheel mouse. With Gutsy, I hadn't this problem. I can rotate the cube with my keybord but not with my wheel house. With hardy , the rotation with my wheel mouse works sometimes: once in five.

My wheel mouse works good with nautilus or firefox... I have a Nvidia 9500gt card. I have the last driver nvidia. i enable viewport switcher.

Maybe, this problem would come from my dual screen.

If you have a idea...

thank you

---

### Post by rune0077 on 2008-06-19
In viewport switcher, does it say "rotate" in the box "Plugin for initiate action"?

And are the Move prev & Move next set to your mousewheel?

---

### Post by Kingorgg on 2008-06-19
On my Ubuntu (8.04) Ctrl+Alt+LMB (Left mouse Button) Rotates my Cube, by Default.

---

### Post by hotwater12 on 2008-06-19
In viewport switcher, there are :
- Name of initiate action = initiate_button 
- Plugin for initiate action =  rotate
- Desktop prev = Button 5 (Mouse wheel down)
- Desktop next = Button 6 (Mouse wheel left)
- Action for starting plugin = button 2 (Mouse middle button)

---

### Post by rune0077 on 2008-06-19
> **hotwater12 said:**
> In viewport switcher, there are :
- Name of initiate action = initiate_button 
- Plugin for initiate action =  rotate
- Desktop prev = Button 5 (Mouse wheel down)
- Desktop next = Button 6 (Mouse wheel left)
- Action for starting plugin = button 2 (Mouse middle button)

That is exactly how mine looks. 

I'm going to state the obvious here, just because I'm not sure what could be wrong: when you use the wheel to rotate, you have to have the mouse-pointer on the desktop - that is, it can't be hovering over another window.

---

### Post by hotwater12 on 2008-06-19
thank you rune0077 for your answer.

But, I have the mouse-pointer on the destkop when i want to rotate my cube, with the wheel.

 I think to my problem  comes from my dual screen. but i'm not sure !!!!

---

### Post by rune0077 on 2008-06-19
> **hotwater12 said:**
> thank you rune0077 for your answer.

But, I have the mouse-pointer on the destkop when i want to rotate my cube, with the wheel.

 I think to my problem  comes from my dual screen. but i'm not sure !!!!

I don't think so. I have dualscreens as well, and no issue. I've got a nvidia-card, so maybe if you have something different. You could always try to disconnect one of the screens to see if that makes a difference.

---

### Post by hotwater12 on 2008-06-20
not difference with one or two screens. 

the rotation with my wheel mouse works sometimes: once in five with one or two screens, it 's strange !

---

### Post by hotwater12 on 2008-06-25
i'am sure that my problem comes from the dual screen. In order to run compiz, i have a script in starting :
```
#!/bin/sh
sleep 6
DISPLAY=:0.0 compiz --only-current-screen --replace &
sleep 6
DISPLAY=:0.0 compiz --only-current-screen --replace &
sleep 9
exec avant-window-navigator

```

if this script doesn't run, i have slow menu in ubuntu, but i can rotate the cube with my wheel mouse !

---

### Post by hotwater12 on 2008-08-08
up :)

thanks

---

### Post by Jaxco on 2008-08-12
how in the world did you get a nvidia driver to work on 8.04 with a 9500gt???? it will not recognize my card at all

---

