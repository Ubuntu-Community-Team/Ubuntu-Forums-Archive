---
title: "Help me with renaming a batch of files with a weird extention! [Resolved]"
date: 2007-01-06
forum: General Help
---

### Post by yuliang on 2007-01-06
I got a batch of files with the extension *mp3;l*. It should be *mp3*. The weired thing is the semicolon. It prevents me using the *rename* command. Anybody has a solution for that?

---

### Post by meng on 2007-01-06
Can you use double quotes, i.e.
rename "example.mp3;l" example.mp3

---

### Post by yuliang on 2007-01-06
No, it doesn't work. I really wonder why linux allow a file extension to have a semicolon in it!:confused:

---

### Post by ButteBlues on 2007-01-06
If all the files in said folder are with that extension:

```
mv ./*.mp3* ./*.mp3
```

Hopefully that should work.

---

### Post by aysiu on 2007-01-06
KRename. [It's in the Universe repositories.](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=krename&searchon=name&subword=1&version=all&release=all)

[http://www.krename.net/Screenshots.11.0.html](http://www.krename.net/Screenshots.11.0.html)

---

### Post by meng on 2007-01-06
Try mv (move) instead of rename. You may need to combine with a script, e.g.

#!/bin/bash
for file in `ls *\;l`; do
mv $file ${file%%;*}
done

(Yes this could be done in the command line itself, but a script is a little easier for testing.)

---

### Post by yuliang on 2007-01-06
Thank all of you.

mv ./*.mp3* ./*.mp3
doesn't work.

Krename works and is easy to use.:)

---

