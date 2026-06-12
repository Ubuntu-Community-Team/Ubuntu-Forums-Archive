---
title: "converting video format to swf.."
date: 2008-03-21
forum: General Help
---

### Post by Mia_tech on 2008-03-21
I'm looking for an app which lets me convert video format like ogg, avi or mpeg to swf...

any help appreciated..

thanks

---

### Post by reyhan on 2008-03-22
try this [[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=567016[/COLOR]]("http://ubuntuforums.org/showthread.php?t=567016")

---

### Post by unutbu on 2008-03-22
```
ffmpeg -i file.wmv  file.swf
```

if you don't have ffmpeg, then you can install it with:
```

sudo apt-get install ffmpeg
```

---

