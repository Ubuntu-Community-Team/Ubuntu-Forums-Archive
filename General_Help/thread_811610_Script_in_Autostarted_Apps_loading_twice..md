---
title: "Script in Autostarted Apps loading twice."
date: 2008-05-29
forum: General Help
---

### Post by stevothewise on 2008-05-29
Basically what I have here is a script that will load Mame when it starts, and once you quit Mame, it will shutdown the computer, and I'm trying to get it so that the script loads on startup, which works fine as of now. the only problem is that when the computer starts up, it loads two instances of Mame. The script looks like this:

```

#/bin/bash

sdlmame
echo mypassword | sudo -S shutdown now -P

```

In Autostarted Apps, this is the only object I have to load on startup.

Anyone know of a way to make it so that the script only loads once? Perhaps how to configure Autostarted Apps without the GUI (I've been using the GUI and maybe its just messing up) as well?

If it matters, I'm running Xfce on Xubuntu 8.04.

Thanks.

---

### Post by stevothewise on 2008-05-31
Problem Fixed.

What was happening was the computer was saving the applications loaded when it shutdown and someone shut it down once without exiting Mame, so 2 versions of the script popped up each time it loaded. 

Which brings me to my next question:

I know I've seen it somewhere before but I can't remember where, how does one disable saving the programs loaded previously?

---

### Post by doorknob60 on 2008-05-31
I don't have Xfce on this computer, but I've seen that option too, it should be somewhere in the Xfce control panel.

---

