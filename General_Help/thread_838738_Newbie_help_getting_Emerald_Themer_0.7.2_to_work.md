---
title: "Newbie help: getting Emerald Themer 0.7.2 to work"
date: 2008-06-23
forum: General Help
---

### Post by sharifi14 on 2008-06-23
Hi there,

I've dipped in and out of Ubuntu over the past few years, but now that Compiz is built-in and ready to use I thought I'd give it another shot.

So far, so good. However, when I try to apply a theme using Emerald Themer 0.7.2 (the file is called 77308-Lowfat Lefty.emerald), the Emerald Themer appears to import the theme but doesn't apply it.

I'm not sure if I'm missing something and would greatly appreciate any help. Apologies if this post is somewhat vague!

Alex

---

### Post by isaacj87 on 2008-06-23
Is emerald running?

Press alt+f2 and type:

```
emerald --replace
```

---

### Post by sharifi14 on 2008-06-24
Cool - that works thanks.

However, will this continue to work when I reboot my computer? I have looked at my processes in System Monitor and Emerald appears to be sleeping.

Thanks again,

Alex

---

### Post by isaacj87 on 2008-06-24
> **sharifi14 said:**
> Cool - that works thanks.

However, will this continue to work when I reboot my computer? I have looked at my processes in System Monitor and Emerald appears to be sleeping.

Thanks again,

Alex

The best thing to do is install the fusion-icon. Set your desired options (i.e. have Emerald be your window decorator) and then just add fusion-icon to sessions.

Run this to install the fusion-icon (it will then be located in Applications->System Tools):

```
sudo apt-get install fusion-icon
```

Or alternatively, if you don't want to install the fusion-icon, you can open up CCSM, go to the "Window Decoration" plugin and where it says "Command" add this:

```
emerald --replace
```

That *should* work too.

---

### Post by sharifi14 on 2008-06-25
Modifying the 'Command' part of the 'Window Decoration' plugin has worked perfectly fine. Thanks for your help mate.

---

### Post by dfmalh on 2008-07-23
Hi, I have the following problem after I installed Emerald... 

I run from a terminal "emerald --replace" which switches my windows manager to Emerald. 

I then open up the compizConfig Settings Manager - System -> Preferences -> Advanced Desktop Effects Settings and select the “Effects” category from the left menu. Click on “Window Decoration” from the selectionin the right pane, and change the present Command (/usr/bin/compiz-decorator) to: /usr/bin/emerald

Then I run the following commands from a terminal for the effects to take place: 

compiz --replace &
emerald --replace &

All works fine until I close my terminal... As soon as I do that, the Titlebar is hidden somehow, I can't close windows, or even drag them.

The only way to see them is to run, which I did by accident... is "emerald --h" running this command from a terminal makes them appear until I close the terminal again... 

Any Idea what is going on?

---

