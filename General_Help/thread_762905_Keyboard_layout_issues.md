---
title: "Keyboard layout issues"
date: 2008-04-22
forum: General Help
---

### Post by Stochastic on 2008-04-22
Hey, so I´ve just installed UbuntuStudio Hardy RC and most went smoothly, but my keyboard layout was detected a bit odd.  It´s listed as US Intl 105 but there are two issues: the first is my right-hand alt button doesn´t work (I think this is a gnome setting if memory serves correct), the second is my ´ key only outputs that if I hit it twice, for instance when I´m typing ¨it´s¨ trying to give me it&#347;.  Essentially I´m getting accentegue (I know I´m spelling that wrong) and umlade marks instead of apostrophe and quotation marks.  Do I need to switch to a PC 104 layout? I looked for an obvious fix in the keyboard settings panel but no luck.  Hëlpá! :(

---

### Post by Achtung on 2008-04-22
It seems both the keyboard model and layout were incorectly set. In the System/preferences/keyboard dialog, select the layouts tab.

In the keyboard model dialog, choose your keyboard model or pick "generic" if your specific model is not listed.

As for the "accents aigüs" (Yes, I use a French-Canadian keyboard ;))... Under the layout, seeing how your Ubuntu forum location specifies Vancouver, you probably have "Canada" listed. Click Add, select "Canada" in Layouts, then pick the "variant" that best represents your keyboard. 

Hope this helps!

---

### Post by Stochastic on 2008-04-22
Yup, that got rid of those frenchie articulations (shakes fist at quebec in a joking manner) but I still am looking to get my right alt key working like the left one does.

Edit: Nevermind, I found the option to "map meta to win keys" hidden in a new place in the keboard layout app.  Now all is well.

---

### Post by Zsola on 2008-04-22
I have a keyboard layout problem too. I am using Ubuntu 7.1, with a Lenovo 3000 N200. I have to accounts on my laptop. With the first one everything is fine, but the other its just not working. I tried to copy all of the settings from the first iser account,  but i got this error message:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10300000

Its the same computer, why does it not working with the second account? Anybody had a similar problem?
Help would be appriciated :)

(yeah i changed from windows, starting to get the hang of Linux. so far i love it ;))
Thx

---

### Post by Zsola on 2008-06-06
Solved that, with playing the gconf-editor with the problematic user account. Just added keyboard layout.

---

### Post by coblenis on 2008-06-18
I have the same problem Stochastic had.  When I tried the solution provided, it worked once.  I then changed the layout option to include "meta is mapped to win-keys." and the solution no longer worked for me.  My keys were back to the double tapping.  I just noticed that if I hold down the space bar while hitting my apostrophe key, the keystroke generates the right symbol (´ + space = ', shift + ´ + space = ").  

I tried restoring the keyboard settings to default then applying the above solution but it did not work.  I would like to know how to fix this because hitting the space bar every time I want to use ['] or  [¨] is awkward and annoying.

---

