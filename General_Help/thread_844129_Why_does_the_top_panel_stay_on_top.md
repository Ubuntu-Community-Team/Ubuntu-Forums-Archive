---
title: "Why does the top panel stay on top?"
date: 2008-06-29
forum: General Help
---

### Post by YMS_1975 on 2008-06-29
Hello,

I'm running Ubuntu 8.04 (Hardy Heron). I've noticed a couple of small annoyances, and I'd like to know how to fix them before they drive me nuts.

The top panel (the one with Applications, Places, System, etc.) always cuts off the top of other applications that open up.

For example: If I go to Applications, then click on Add/Remove to install any software, the dialog box will open up for me to add/remove software (as it should). The problem however is that the top panel cuts off the text from the Add/Remove dialog box. So where it says "Show: All Available Applications" and "Search"; the top half of it's cut off. ](*,)

Also...there's no minimize, maximize or close buttons. The only way to close any open window is to right click on the taskbar item and select close. And moving a window around? Forget about it. I can't do that either.

What gives?

---

### Post by sdennie on 2008-06-29
Are you running compiz (Desktop Effects)?  It sounds like you might not have the Place module enabled.  Try:

```

sudo apt-get install compizconfig-settings-manager

```

Then, go to System->Preferences->Advanced Desktop Effects and scroll down towards the bottom.  Ensure that Place Windows is enabled.

---

### Post by YMS_1975 on 2008-06-29
> **vor said:**
> Are you running compiz (Desktop Effects)?  It sounds like you might not have the Place module enabled.  Try:

```

sudo apt-get install compizconfig-settings-manager

```

Then, go to System->Preferences->Advanced Desktop Effects and scroll down towards the bottom.  Ensure that Place Windows is enabled.


Well, I tried what you suggested. That did make it a bit better. But I still can't seem to minimize, maximize or move my windows around. I can minimize & maximize if I right click on the taskbar button.

If you've got any more ideas....I'm listening. :)

---

### Post by YMS_1975 on 2008-06-29
You know what? Nevermind.

It's the weirdest thing. I tried switching back to "Normal" under the Visual Effects dialog box, and the minimize, maximize & close buttons all appeared.

Then I tried switching back to "Extra" and it worked great. I've got the buttons now and I'm able to move the windows around.

I guess Hardy Heron just had her feathers ruffled just a bit. :)

---

