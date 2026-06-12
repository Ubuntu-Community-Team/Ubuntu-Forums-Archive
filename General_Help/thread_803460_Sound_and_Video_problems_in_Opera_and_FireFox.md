---
title: "Sound and Video problems in Opera and FireFox"
date: 2008-05-22
forum: General Help
---

### Post by Deadheded on 2008-05-22
Upgraded to 8.04 but had this same problem in all previous versions back to 6.06.  This is my 2nd computer since then so it is not a hardware thing.  

Using Opera 9.27 and the latest FireFox.  When I go to play an online video, such as any youtube video, I get no video and no sound in Opera.  In FireFox I get video but no sound.

Video and sound work great for any video or sound file not online.

I have flash installed

---

### Post by Deadheded on 2008-05-30
Anyone have any idea or at leaste some place for me to start?

---

### Post by Colonel Kilkenny on 2008-05-30
Flash version which Ubuntu ships with is not compatible with Opera 9.27. Easiest way to get a working flash in Opera is to fetch Opera 9.50 Beta 2 from opera.com.

And Firefox (and flash audio) needs probably libflashsupport. 
"sudo aptitude install libflashsupport" should do the trick. Although for some users libflashsupport apparently causes Firefox to crash. No problems with Opera.

---

### Post by zvacet on 2008-05-30
You can download older flash version [here #13]("http://ubuntuforums.org/showthread.php?t=745325&page=2")

---

### Post by Deadheded on 2008-06-03
Thanks much did the trick for FireFox.  That is all I really need...

---

