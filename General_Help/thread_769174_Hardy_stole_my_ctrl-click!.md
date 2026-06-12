---
title: "Hardy stole my ctrl-click!"
date: 2008-04-26
forum: General Help
---

### Post by chrismar on 2008-04-26
Hello there,

This morning I upgraded from feisty to hardy.  Everything went smooth and my wireless even works flawlessly now (yay!), however I do have 1 very annoying problem:

I can't ctrl-click to open a link in a new tab in firefox.  Apparently hardy wants to use the ctrl-click to move windows.  I don't want ctrl-click to move windows, I want it to open tabs!

I can't find this "ctrl-click" setting anywhere in the keyboard shortcuts, nor can I even find such a thing as a mouse shortcuts panel.

What can I do?  I want my ctrl-click back!

Thanks in advance!

---

### Post by ibuclaw on 2008-04-26
I am guessing that you have Compiz enabled, am I right?

If so, try going into the desktop effects menu:
**"System>Preferences>Advanced Desktop Effect Settings"**

Scroll down to the bottom of the new window. And under the Banner:
> ? Uncategorised
Click on the "**Move Window**" Picure (don't disable it just yet).

This will open up the settings for that option.

If the first setting (Initiate Window Move) with a picture of a mouse beside it has a command button that says:
```
<Control>Button1
```
Then click on the button and change it to just "ALT" (Have it being the only one in green).

[[IMG]http://img134.imageshack.us/img134/2430/screenshotqz5.th.png[/IMG]](http://img134.imageshack.us/my.php?image=screenshotqz5.png)

Regards
Iain

---

### Post by RainCT on 2008-04-26
This might be caused by Compiz. Try if ctrl+click works if you disable the desktop effects, and if it does then you'll have to find the shortcut in compizconfig-settings-manager and change it to something else.

---

### Post by chrismar on 2008-04-26
I don't have compiz enabled, actually. :(

I tried what you said anyway, and now it doesn't move, but it doesn't behave properly either.

---

### Post by ajgreeny on 2008-04-26
Try using the firefox add-on Tab-Mix-Plus.  It allows you to set a great number of different tab browsing options, and is one of the first I like to add to the browser every time.  You can then set to open whatever links you want as new tabs.

---

### Post by chrismar on 2008-04-26
Restarting the x server seems to have fixed it up.  Thanks!

---

