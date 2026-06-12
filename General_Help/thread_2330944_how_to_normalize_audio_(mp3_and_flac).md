---
title: "how to normalize audio (mp3 and flac)"
date: 2016-07-16
forum: General Help
---

### Post by palmgrower on 2016-07-16
What program can I use to normalize mp3 and flac. I am fine with 2 different programs for these two types.
All music files are in desktop > Music.
Ubuntu 16.04

Thanks.

EDIT: I searched this forum. I can use Audacity to normalize flac. What about mp3? If I use Audacity, mp3 will be converted to a project and converted back to mp3. Is there a way to normalize mp3 without type conversion?

EDIT: I found replaygain simple to use in 16.04
replaygain *.mp3 or
replaygain --force *.mp3 (if ID tag is not present)
replaygain -f *.mp3 (same as above)
replaygain *.flac;

EDIT 2: replaygain does not seem to normalize well. I used mp3 gain. This can be installed per [https://launchpad.net/~flexiondotorg/+archive/ubuntu/audio](https://launchpad.net/~flexiondotorg/+archive/ubuntu/audio). After adding it to repository, sudo apt-get install mp3gain. Easymp3gain is in 16.04 repository. If time is indication of effectiveness, mp3gain takes a lot longer than replaygain. Also, mp3 files checked thru replaygain come out blank (no gain adjustment) in mp3gain.

---

### Post by QDR06VV9 on 2016-07-16
Have  a look here: [http://askubuntu.com/questions/246242/how-to-normalize-sound-in-mp3-files](http://askubuntu.com/questions/246242/how-to-normalize-sound-in-mp3-files)

---

