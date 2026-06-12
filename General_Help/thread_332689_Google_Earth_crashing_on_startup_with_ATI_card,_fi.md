---
title: "Google Earth crashing on startup with ATI card, fixed."
date: 2007-01-06
forum: General Help
---

### Post by tenjin1 on 2007-01-06
Just wanted to post my fix to the problem with Google Earth crashing on startup.
This is only meant for the problem with people using ATI card using the libGL.so.1. Thanks to **gala** at [http://www.ubuntuforums.org/showthread.php?t=296131&highlight=google+earth+crashes+on+startup]("http://www.ubuntuforums.org/showthread.php?t=296131&highlight=google+earth+crashes+on+startup")
for providing the link to the fix.

First, I installed Google Earth on my machine by typing this in terminal:
```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```
then followed the directions for install.

After installed, I would start GE and see the splash screen starting up then that was it...nothing else, it wouldn't start. I read this was a problem with people using ATI graphics card and something to do with the GL driver.
Following the instrucions at [http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/683541/page/vc/vc/1]("http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/683541/page/vc/vc/1"),  and this is **exactly** what I did on my machine to get it to work:

First I grabbed the file libGL.so.1.2 in /usr/lib/i686/mmx/cmov
you can seach for this file by typing in terminal:
```
locate libGL.so.1.2
```
the file was also in /usr/lib and another place i think, but for some reason that one didn't work for me

so in a Terminal:
```
cd /usr/lib/i686/mmx/cmov
```

then we want to copy the libGL.so.1.2 into our google earth directory (which mine is in my Home directory and it will be if you installed GE with command above, otherwise the rest of these commands may not work):
```
sudo cp libGL.so.1.2 ~/google-earth
```

then:
```
cd ~/google-earth
```

then change permission of that file from root to you:
```
sudo chown "your_username-here" libGL.so.1.2
``` 

Now rename the file by dropping the ".2" on the end:
```
mv -v libGL.so.1.2 libGL.so.1
```

now start Google Earth ans should start initializing. This worked perfectly on my machine. Is a little slow but other than that is working great. Hope it works for you too.:D

> CAUTION: Do not be tempted to overwrite /usr/lib/libGL.so.1.2 or /usr/lib/i686/mmx/cmov/libGL.so.1.2 or any other instance of the library already in place, as you might brake OpenGL support for other applications.

---

### Post by maestrobwh1 on 2007-03-11
I was hopeful, and did this as I have an Ati radeon card and I had the same issue, but alas, this did not fix it.  Thanks tho!

---

