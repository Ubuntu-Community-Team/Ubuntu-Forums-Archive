---
title: "Script question and resizing photos"
date: 2007-01-24
forum: General Help
---

### Post by Grog140 on 2007-01-24
Alright, tell me if this is possible.

To make some sort of nautilus script to:

-Resize a photo to 20% of its original size
-Save the resized photo as a new name but keep the original
-Do that with all the photos in the directory

Alright, I don't know where to begin but but can someone tell me before I try if it is possible? I have never made an automatic thing in my life.

Thanks

---

### Post by aidanr on 2007-01-25
something like

```
#!/bin/bash
convert "$@" -resize 20% resized.jpg
```

should do the trick, the $@ is the files you select and when you select multiple files they'll be output as resized-0.jpg resized-1.jpg etc
you'll need to select all the files in the directory you want to process though, if you select one at a time it'll overwrite the output file

---

### Post by Grog140 on 2007-01-25
Wow...Thanks. I need to learn how to do this.

Anyway, I am running into a little bit of a problem. For some reason that I don't know, it works fine with a few files (2-8) but if I do about 40 my computer locks up and I need to reboot.

Also, how would I go about just renaming all the files by number. For example if I had kgh.JPG and hjg.JPG, I want to rename them both to pic1.jpg and pic2.jpg.

Thanks again

---

### Post by aidanr on 2007-01-25
i think the convert program is pretty resource intensive, i was running it the other night to resize and compress about 40 files and the computer was practically unusable for 10 minutes

maybe you can make it so the script runs at a lower priority (nice -n 3 convert "$@" -resize 20% resized.jpg) and also you can look at other scripts to see how to do a progress dialog and how to make it rename the files like you want, tbh the above is about the height of what i know atm

anyway heres a couple of links to get started

[http://g-scripts.sourceforge.net/faq.php](http://g-scripts.sourceforge.net/faq.php)
[http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php)

---

