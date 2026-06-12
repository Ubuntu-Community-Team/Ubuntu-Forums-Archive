---
title: "Require Help With 'devilspie' Scripting"
date: 2006-07-31
forum: General Help
---

### Post by BitTorrentBuddha on 2006-07-31
Hey, I've always been kind of annoyed by azureus' main window not maximizing when I open it. A google the other day showed me the way to devilspie. Being a bit of a control freak with my desktop, and enjoying simple scripting, I felt it would appeal to me. After a couple minutes of glancing through the tutorial, I started making some scripts. I have it working with one application the way I would like, easytag, however none of the other scripts seem to work (neither my center system monitor one nor my maximize azureus one.) Tell me if this looks wrong on the (not so) off chance that I just didn't do things right: ```
(if
        (is (window_name) "Azureus")
(maximize))
```
Also could somebody point me to a more verbose tutorial than [this](http://wiki.foosel.net/linux/devilspie)? How would I find a window's window_role? Also, would application_name work for programs that are compiled?

PS: How do I end a process running in a terminal without opening the system monitor or using a different one to killall it, is there a shortcut (such as ctrl+z to stop a process.)

---

### Post by BitTorrentBuddha on 2006-07-31
:(

---

### Post by BitTorrentBuddha on 2006-08-04
I solved out the azureus problem by changing is to contains. The other questions all still stand if anyone could assist.

---

### Post by argie on 2006-08-05
> How do I end a process running in a terminal
Ctrl+C perhaps?

---

### Post by jeff_ on 2006-08-05
[http://www.ubuntuforums.org/showthread.php?t=75749](http://www.ubuntuforums.org/showthread.php?t=75749) is a great tutorial.

---

