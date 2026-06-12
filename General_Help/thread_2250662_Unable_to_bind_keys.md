---
title: "Unable to bind keys"
date: 2014-10-30
forum: General Help
---

### Post by FreedomOverdose on 2014-10-30
Hello everyone, 

I'm using ubuntu 14.10 with i3wm, and I'm trying to bind super+space to kupfer. For some reason, most of the time the keybinding fails (sometimes it randomly works though).

That shortcut isn't being used by unity (and unity-settings-daemon/gnome-settings-daemon aren't running). When I try to bind the key with xbindkeys I get the following message:
```

Please verify that there is not another program running
which captures one of the keys captured by xbindkeys.
It seems that there is a conflict, and xbindkeys can't
grab all the keys defined in its configuration file.
```

So it seems like something is already bound to those keys, but I have no idea what it is.

What's the best way to debug this? Is there an easy way to find out what process is registered to receive a particular keypress event?

Thanks in advance!

---

### Post by JazzPotato on 2014-10-30
I tried multiple methods of rebinding keys and the best one I found was to create a custom Xmodmap file and load it at boot.
For example, my ~/.Xmodmap
```

remove Lock = Caps_Lock
keysym Caps_Lock = Escape

```
I am using this to remap caps lock to escape, however you can remap any key to anything by running the command:
```

xev

```
Which will show you the keycodes of the keys you are pressing. 
I'm sure there's a good tutorial out there for making and using Xmodmap files which explains things better than I can now, so just do a quick google.
This is really the most foolproof way of doing it, and even though it might be trickier to set up it will save you headaches in the future.
Good Luck!

---

### Post by FreedomOverdose on 2014-10-30
Thanks for your reply! Unfortunately I don't think xmodmap will work if I want to bind a chord (in this case super + space) to a custom command; as xbindkeys is saying, something is already grabbing those keys, I just need to find out what it is and unbind it :/

---

