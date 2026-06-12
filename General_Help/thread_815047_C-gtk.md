---
title: "C-gtk"
date: 2008-06-01
forum: General Help
---

### Post by madara_sama on 2008-06-01
Hi guys, I want to start learn GTK using C. But I dunno how to do.
I got the tutor from GTK web. But, I cant..
Something wrong, path? (I'm not sure)
The errors from include the library.
#include <gtk/gtk.h>
I checked the path, but there's no folder named gtk, but gtk2.0.
I changed to gtk2.0/gtk.h, but still the same.

So, here...
I asked u (more experience than me) :
>>What do I need to start GTK using C?
please explain to me in condition : ubuntu fresh install
what files do I need to install??



TQ
__

---

### Post by unutbu on 2008-06-01
I think you need build-essential and libgtk2.0-dev to compile gtk programs.
```

sudo apt-get install build-essential
sudo apt-get install libgtk2.0-dev
```

You may also find the gtk2.0-examples package useful -- it has lots of little programs which demonstrate the various widgets you can use.
```
sudo apt-get install gtk2.0-examples
```

---

### Post by madara_sama on 2008-06-01
Is that?? Only that files..?
It's for condition ubuntu fresh install..

---

