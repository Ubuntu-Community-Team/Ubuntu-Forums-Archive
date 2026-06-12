---
title: "Compiz Emerald Themes"
date: 2008-05-12
forum: General Help
---

### Post by amtur_poet on 2008-05-12
I have installed a few themes in compiz emerald, but nothing happens when I click on them. What should I do to make them load? I am using Ubuntu 8.04 Hardy.

---

### Post by chadwit on 2008-05-12
EXACTLY.....I'm doing the same thing trying to figure out how to apply these things. I know my post doesn't answer your question, but would somebody PLEASE explain how to apply these themes in Emerald?

Thank you!!!

---

### Post by techstop on 2008-05-12
Have you installed ccsm?

EDIT: If not;

```
sudo apt-get install compizconfig-settings-manager
```

If so, open it up and go to General Options. Click on Window Decoration plugin and in the command text box, enter this command;

```
emerald --replace
```

Restart and try to change a theme from emerald...

---

### Post by chadwit on 2008-05-13
I see no Window "Decoration plugin" -  I just have tabs "Info,Animations,Effects,Desktop,Accessability,Edges". Is there another piece I need to install?

---

### Post by techstop on 2008-05-13
> **chadwit said:**
> I see no Window "Decoration plugin" -  I just have tabs "Info,Animations,Effects,Desktop,Accessability,Edges". Is there another piece I need to install?

I'm not even sure what menu you are looking at with those options...

If you have installed compizconfig-settings-manager as above, then you open it up using the System menu on your panel, then select Preferences, then Advanced Desktop Effects Settings.

You will then get a number of options split into categories, Window Decoration is under the Effects category.

---

### Post by Enlitend on 2008-05-13
I think chadwit was talking about the Simple Compiz Config Settings Manager.

chad, you need the other one, just follow techstop's code from the above and you should be good to go.

After installation, it should be on
 System->Preference-->Advanced Desktop Effects Settings

---

### Post by chadwit on 2008-05-13
The tabs I was referring to are in System->Preferences "Simple CompizConfig Settings Manager". I guess that's the confusion as you said. OK - now were' getting somewhere. So I put "emerald --replace" in the command field. I open up Emerald themer. How do I activate any of the themes in the list? Do I need to restart Compiz for the new command to take effect? If so, how do I do that?

---

### Post by techstop on 2008-05-13
> **chadwit said:**
> The tabs I was referring to are in System->Preferences "Simple CompizConfig Settings Manager". I guess that's the confusion as you said. OK - now were' getting somewhere. So I put "emerald --replace" in the command field. I open up Emerald themer. How do I activate any of the themes in the list? Do I need to restart Compiz for the new command to take effect? If so, how do I do that?

Press Alt+F2, then type "emerald --replace" (without the quotes) and press enter.

---

### Post by chadwit on 2008-05-13
That worked! Wow! it's amazing how you guys know this stuff! I never would have figured this out on my own...one final question: If I want to revert back to my original manager, am I correct in assuming I can just do the alt+F2 thing again? What was the original syntax? (It was gtk something I think...)

---

### Post by techstop on 2008-05-13
> **chadwit said:**
> That worked! Wow! it's amazing how you guys know this stuff! I never would have figured this out on my own...one final question: If I want to revert back to my original manager, am I correct in assuming I can just do the alt+F2 thing again? What was the original syntax? (It was gtk something I think...)

AFAIK (not at my linux pc now), you would use;

```
compiz --replace
```

to stop using emerald.

I also knocked up a quick blog post (with screenshots) about customising compiz, installing ccsm, installing emerald and themes, and customising your mouse cursor. You can find it here;

[http://techstop.com.au/2008/05/compiz-tips-ccsm-emerald-and-mouse-pointers/](http://techstop.com.au/2008/05/compiz-tips-ccsm-emerald-and-mouse-pointers/)

---

### Post by chadwit on 2008-05-13
Thanks guys - I really appreciate all of your help. If you're ever in Chicago, beers on me!!!

---

### Post by Tenken on 2008-05-13
If you're going to be switching between window manager at all, try installing the fusion-icon

```
sudo apt-get install fusion-icon
```

Once loaded it shows up in your tray and lets you choose your decorator (emerald, metacity, etc) and is a short cut to the configuration manager if you have it installed.

---

### Post by dasunsrule32 on 2008-05-13
> **Tenken said:**
> If you're going to be switching between window manager at all, try installing the fusion-icon

```
sudo apt-get install fusion-icon
```

Once loaded it shows up in your tray and lets you choose your decorator (emerald, metacity, etc) and is a short cut to the configuration manager if you have it installed.

It will only start if you have it in your 'Sessions'. Go to System -> Preferences -> Sessions, click add. Call it whatever you want, then in the command line, put: 
```

fusion-icon --no-start

```

That will start it and not have it replace any window manager because you already changed that with the advanced settings manager. Hope that helps.

---

### Post by r5gtt2k3 on 2008-05-14
> **techstop said:**
> AFAIK (not at my linux pc now), you would use;

```
compiz --replace
```

to stop using emerald.

I also knocked up a quick blog post (with screenshots) about customising compiz, installing ccsm, installing emerald and themes, and customising your mouse cursor. You can find it here;

[http://techstop.com.au/2008/05/compiz-tips-ccsm-emerald-and-mouse-pointers/](http://techstop.com.au/2008/05/compiz-tips-ccsm-emerald-and-mouse-pointers/)


Nice page you got there, Using it now :) Even I (noob) can understand it, Thanks again

---

### Post by techstop on 2008-05-14
> **r5gtt2k3 said:**
> Nice page you got there, Using it now :) Even I (noob) can understand it, Thanks again

Cheers!

---

### Post by charlemagne86 on 2008-05-22
just in case someone else like me wanders off and is wondering where to find that illusive(duh!) "window decoration"...its in the effects part of ccsm!

---

### Post by charlemagne86 on 2008-05-22
btw, dunno if its the right place to post....sorry mods!!

but can anyone direct me to some good looking themes that say out 'linux'......wherever i search (beryl-themes. gnome-look etc...) the themes are either winXP/Vista/MacOS spinoffs..(which i dont want) or either not good enough visualy!!


thnx!

---

### Post by Zigsaw on 2008-10-31
thanks...

solved...

alt+f2..run emerald --replace

and then logout..login

other way

system>>preferences>>advanced desktop effects>>effects>>window decorator>>command..
by default it will be /usr/bin/compiz
change it to emerald --replace as usual logout..login

---

### Post by Hoobes1 on 2009-01-04
One simple thing that you can do, is just getting "compiz-fusion" from add/remove. Run it from "applications -> system tools -> compiz-fusion", then right click on the icon that appears next to the network connection, and other stuff, and under "select window decorator", you click on emerald. Make sure that "select window manager", which can be found under the right click menu, is on compiz. Voala, you have your emerald window theme! ^^......ok, in the end it doesn't sound that simple, but if you do it your self, you have a better overview of what's going on than when you put in commands on the terminal. Hope this helped! =D

---

