---
title: "Need to know the Repo's for Snow"
date: 2008-06-25
forum: General Help
---

### Post by phoenixankit on 2008-06-25
I need to know which repos I need to add to get the following:

compiz-fusion-plugins-unofficial
compiz-fusion-plugins-unsupported



[B]EDIT:
I installed the script from this topic:
[http://ubuntuforums.org/showthread.php?t=820802](http://ubuntuforums.org/showthread.php?t=820802)

Does the script cover all the Plugins from 
compiz-fusion-plugins-unofficial
compiz-fusion-plugins-unsupported?

EDIT 2:
I'm getting this error:(look in the attachments)
What is this? Why am I getting this? What is not installed and what is?[/B]

---

### Post by phoenixankit on 2008-06-26
Someone please help!

---

### Post by isaacj87 on 2008-06-26
I took a peek into the error report. You seem to be missing some "cairo-xlib" package as can be seen here in the error output:

> 
Makefile:58: *** [ERROR] No package 'cairo-xlib' found.  Stop.
Makefile:58: *** [ERROR] No package 'cairo-xlib' found.  Stop.

Please run this command in terminal and try the script again:

```
sudo apt-get install libcairo2 libcairo2-dev libcairomm-1.0-1 libcairo-perl libcairo-ruby1.8 libglitz1 libmono-cairo1.0-cil libmono-cairo2.0-cil libpixman-1-0 libpixman-1-dev python-cairo
```

Here's the [post]("http://ubuntuforums.org/showpost.php?p=5166863&postcount=33") I got the info from, but I kind of figured since I compiled my own Compiz Fusion. Hope this helps!

---

### Post by phoenixankit on 2008-06-26
Thanks for the reply, I'll boot into Mint and tell you the results.

---

### Post by phoenixankit on 2008-06-26
Ya, the cairo problem has been solved, but the firefly, star, and snow packages are still producing error.

What exactly was that Cairo thing?

EDIT: I've installed 'Elements' plugin, so I dont need the Firefly,Star and Snow. Thanks!
Can you tell me were these*[ Anaglyph, Atlantis, Atlantis2, Fireflies, Freewins, Photowheel, Screensaver, Snow, Snowglobe, Stars, Tile, and Wallpaper]*the only plugins present in

compiz-fusion-plugins-unofficial
compiz-fusion-plugins-unsupported

---

