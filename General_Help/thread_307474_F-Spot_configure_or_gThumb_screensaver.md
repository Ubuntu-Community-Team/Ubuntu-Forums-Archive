---
title: "F-Spot configure or gThumb screensaver?"
date: 2006-11-26
forum: General Help
---

### Post by Mr. Picklesworth on 2006-11-26
Both F-Spot and gThumb are useless to me without two trivial features.

1. Can I configure how long it takes to switch images in the F-Spot slideshow mode? I checked the bug database and found that someone has made a patch for this, but I don't feel like compiling it from source. I hunted through my home folder and found .gconf/apps/f-spot/, in which there are a few XML files such as in a subdirectory called screensaver. The one in screensaver contains```
<?xml version="1.0"?>
<gconf>
        <entry name="tag_id" mtime="1163983487" type="int" value="7">
        </entry>
</gconf>
```and looks rather useless at first glance... and it doesn't seem to be documented!
Perhaps I can change the timer with this file, though?

2. Is there a gThumb screensaver? It does the management stuff I want (although with less style than F-Spot) and the developers are not afraid of having more than one item in the preferences window (that window where you are *supposed to be able to configure stuff*), but the lack of a screensaver mode seems silly.
Have I missed something, or is there an unofficial gThumb screensaver somewhere?

Thanks in advance!

---

### Post by slacker9876 on 2007-07-11
Here here! If I were a developer I would add this feature, but rather I ask ....

Is the fspot slide disply time configurable? I have just imported a ton of photos and would love to use them, but 1 second seems too little. Any help is appreciated!

---

