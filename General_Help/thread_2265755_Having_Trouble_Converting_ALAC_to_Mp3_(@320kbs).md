---
title: "Having Trouble Converting ALAC to Mp3 (@320kbs)"
date: 2015-02-17
forum: General Help
---

### Post by jooge on 2015-02-17
I usually use SondConverter to convert all my music files if I need to, but it appears that it will not convert ALAC to Mp3. Does anyone know of another program that can do this? Thanks in advance.

---

### Post by ajgreeny on 2015-02-17
Try winff.

I use it sometimes but I don't have any ALAC files to try on it and I have no idea about ALACs.

I have no idea if avconv can even read ALAC but you could also try avconv in terminal with command ```
avconv -i file.ALAC -acodec libmp3lame -ab k file.mp3
```which works fine on a flac file to convert it to mp3 at 320kb/s.

As another way, you could try to **convert** the files in VLC, which will apparently play ALAC files, but you will need to set that high 320kb/s output first.

---

