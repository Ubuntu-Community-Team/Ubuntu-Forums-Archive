---
title: "Finding installed apps in 8.04"
date: 2008-06-13
forum: General Help
---

### Post by mamboze on 2008-06-13
I've installed two apps on 8.04 - Kodos from synaptic and hardinfo using sudo apt-get install hardinfo. 

But I can't find either of them. I've looked thru Applications Edit Menus and Add/Remove Applications but no show. So, is there another place I should look or something else to be done. 

thanks in advance for any help

---

### Post by Zorael on 2008-06-13
It looks to be a terminal program. Is it?

If so, it will likely not show up under Applications unless you create your own launcher for it. There should be a check box in the window to create launchers that allow you to make the program run in a terminal, which is basically what you want it to do.

If it *isn't* a terminal program, well, ignore me.

---

### Post by ph1 on 2008-06-13
If you're looking for a script to run or something try 

```
whereis <programname>
```

in the terminal.  Usually it can turn up something for you.

---

### Post by mamboze on 2008-06-13
Both have GUIs. On running whereis for both, I got these outputs

kodos: /usr/bin/kodos /usr/share/kodos /usr/share/man/man1/kodos.1.gz
hardinfo: /usr/bin/hardinfo /usr/lib/hardinfo /usr/share/hardinfo /usr/share/man/man1/hardinfo.1.gz

So I guess I have to extract them and then install?

---

### Post by mamboze on 2008-06-13
Ok, I checked out the usr/bin folder and found the two executables and they worked fine. [http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)

thanks for your help  [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by bazcor on 2008-06-13
hardinfo installed a entry under System/Preferences/System Profiler and Benchmark on my Hardy install

---

