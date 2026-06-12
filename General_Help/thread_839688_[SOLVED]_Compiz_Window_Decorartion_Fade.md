---
title: "[SOLVED] Compiz Window Decorartion Fade"
date: 2008-06-24
forum: General Help
---

### Post by MeanEYE on 2008-06-24
Hi,

I have this minor issue with compiz and I cant find the option to turn it off. 

It's about window decoration. While using compiz window decoration plugin, inactive windows will have their border faded. I want to turn this off... 

Is this possible and how!

Thanx!

---

### Post by rico002 on 2008-06-24
> **MeanEYE said:**
> Hi,

I have this minor issue with compiz and I cant find the option to turn it off. 

It's about window decoration. While using compiz window decoration plugin, inactive windows will have their border faded. I want to turn this off... 

Is this possible and how!

Thanx!

i have the same problem....like the minimize, exit, and maximize buttons are gone right? (the whole border too)

---

### Post by bigstras on 2008-06-24
It sounds like you are both having a problem with emerald and not compiz.  
@meaneye:  
Go to System -> Preferences -> Emerald Theme Manager, click on edit themes and look around in the settings there to find the specific value; as there are different "frame engines", the theme you use may not have the same settings as mine.  I use a theme that uses the pixmap engine, and the way to change how inactive window border acts is under the titlebar tab.
If that is not the problem, it could be that you are using a plugin in compiz that produces the undesired effects: ADDHelper and Trailfocus are two that pop out off the top of my head.

@rico002: 
Alt+F2 and type in: ```
emerald --replace
``` 
this should fix the problem anytime your window decoration seems to disappear _if_ you are using emerald for your window decorator.  
Otherwise Alt+F2 and type ```
gtk-window-decorator --replace
```

---

### Post by rico002 on 2008-06-24
i dont have emerald theme manager i have ubuntu 8.04 and i did the decorator command and nothing happens

---

### Post by MeanEYE on 2008-06-25
@rico002:
No everything is there just faded... Alpha is not 100% but ~70%, when I click on the window (set focus on it), border becames fully visible (not faded, 100% alpha).

@bigstras:
This is not acutally a problem. Cuz I see the window border, just it's transparend on unfocused windows and normal on focused window. Clearly it's just a matter of configuration, but am interested how to change that so my borders are always 100% alpha.

---

### Post by bigstras on 2008-06-25
> **MeanEYE said:**
> 
@bigstras:
This is not acutally a problem. Cuz I see the window border, just it's transparend on unfocused windows and normal on focused window. Clearly it's just a matter of configuration, but am interested how to change that so my borders are always 100% alpha.

I didnt mean to imply that yours and rico's problems were the same in my post.  Its just the fact that its **only** your window borders fading when unfocused leads me to think it has something to do with the window decorator you are using rather than compiz - AFAIK, there is no option in compiz that will change that behavior, but there is one in emerald theme manager.

What window decorator are you using? What theme?
Are you using any of the following plugins for compiz: trailfocus, ADD helper, opacity?
If so, turn them off and see if that fixes your problem.

---

### Post by MeanEYE on 2008-06-25
Am using trailfocus but the effect remains the same even after I turn that plugin off. Not sure what window decorator am using, have to check that one when I get home. When I think of it better it just might be that is the problem, in window decorator. Cus there are no effects when fading window decorations (border).

Thanx for your swift reply. I appriciate that. Soon I'll be home and check that right away, and let you know... thanx! :)

---

### Post by bigstras on 2008-06-25
to try to figure out which decorator you are using, try these two commands in the terminal:
```
ps aux | grep emerald
```
```
ps aux | grep gtk-window-decorator
```

if you find you are using emerald, refer to my first post when you want to try to fix it.

---

### Post by MeanEYE on 2008-06-25
Now this is weird :)

```
root@Bytewiper:/home/meaneye# ps aux | grep emerald
root      8382  0.0  0.0   5164   844 pts/0    R+   19:47   0:00 grep emerald
root@Bytewiper:/home/meaneye# ps aux | grep gtk-window-decorator
meaneye   5988  0.0  0.5 148904 11360 ?        S    15:40   0:00 /usr/bin/gtk-window-decorator
root      8384  0.0  0.0   5164   844 pts/0    R+   19:47   0:00 grep gtk-window-decorator

```

In Window Decoration plugin in compiz under Command it says "/usr/bin/compiz-decorator"...

---

### Post by bigstras on 2008-06-25
you are using gtk window decorator.  

try this: 
Alt+F2 and open gconf-editor
navigate to /apps/gwd/
change metacity_theme_opacity to 1

That should do it.  i tried it here and could go back and forth from having variously transparent window borders.

---

### Post by MeanEYE on 2008-06-25
> **bigstras said:**
> you are using gtk window decorator.  

try this: 
Alt+F2 and open gconf-editor
navigate to /apps/gwd/
change metacity_theme_opacity to 1

That should do it.  i tried it here and could go back and forth from having variously transparent window borders.

Yeaah, baby... thats the stuff am talking about :D

Thanx man... I tought there were some option to turn that off since I did that once before and cant remember how :). I looked in config before posting this actually but never have tought about conf group named GWD :)... 

Thanx once more ;)

---

### Post by ericesque on 2008-07-29
been looking for this for a while.  Just doubled by satisfaction with the theme I've put together!  Thanks all!!

---

