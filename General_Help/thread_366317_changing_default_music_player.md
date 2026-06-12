---
title: "changing default music player"
date: 2007-02-20
forum: General Help
---

### Post by 13east on 2007-02-20
i just bought a new keyboard (Logitech Cordless Desktop S510) and I'm trying to program all the keys.  I have one of the keys set to launch the default music player (through "keyboard shortcuts" under "system -> preference") and it keeps launching rhythmbox music player.  i want it to launch xmms and i have it set as the default player for mp3.  i just can't find the option to change this setting.  some help would be much appreciated.  thank you.

---

### Post by bruenig on 2007-02-20
One of the unfortunate limitations of gnome. What I would do is install xbindkeys
```
sudo apt-get install xbindkeys xbindkeys-config
```

Then from the terminal launch xbindkeys
```
xbindkeys-config
```

It will tell you to do something the first time you launch it, just copy and paste what it tells you to do and then launch it again
```
xbindkeys-config
```

From there, there is a very easy to use gui, just create a shortcut for the command "xmms" and then use that instead of the default music player setting through gnome.

To make sure xbindkeys is running, you can run "xbindkeys" and a good practice is to add that command to the System>Preferences>sessions startup commands tab.

---

### Post by 13east on 2007-02-20
thx bruenig, i'll try this when i get back on my desktop.

---

### Post by mgmiller on 2007-02-20
You can try installing keytouch.  I think that will give you a lot more options for setting up the shortcut keys on your keyboard.  It's in the Universe repository, so make sure that is enabled.  Then just:
```

sudo apt-get install keytouch
```

Hope that helps.

Good Luck

---

### Post by 13east on 2007-02-21
> **mgmiller said:**
> You can try installing keytouch.  I think that will give you a lot more options for setting up the shortcut keys on your keyboard.  It's in the Universe repository, so make sure that is enabled.  Then just:
```

sudo apt-get install keytouch
```

Hope that helps.

Good Luck

when i install keytouch, it makes me setup keyboard preference but can't seem to find my keyboard (logitech cordless desktop s510) in their list.  where can i find one for my keyboard?

---

