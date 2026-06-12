---
title: "Script to convert mp3 files to smaller sample rate?"
date: 2008-05-24
forum: General Help
---

### Post by chadk on 2008-05-24
I've been searching for hours.  I've found several examples of converting FLAC to OGG to MP3, etc.,  but I just want to make large files smaller by reducing the quality for my daughter's mp3 player.  Is there a script or something I can use to do this?  I've tried using Soundconverter but the thing either makes 0 byte files or just hangs there for hours on a single song and never does anything.

---

### Post by chadk on 2008-05-24
> **chadk said:**
> I've been searching for hours.  I've found several examples of converting FLAC to OGG to MP3, etc.,  but I just want to make large files smaller by reducing the quality for my daughter's mp3 player.  Is there a script or something I can use to do this?  I've tried using Soundconverter but the thing either makes 0 byte files or just hangs there for hours on a single song and never does anything.

Found this script in my old home directory:
mkdir smaller
find -maxdepth 1 -type f -name '*.mp3' -exec lame -b80 -q0 '{}' -o 'smaller/{}' \;

---

