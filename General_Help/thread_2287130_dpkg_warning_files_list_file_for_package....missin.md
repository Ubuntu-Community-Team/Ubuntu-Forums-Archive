---
title: "dpkg: warning: files list file for package....missing; assuming package has no files"
date: 2015-07-17
forum: General Help
---

### Post by sashhhh on 2015-07-17
I keep getting this message when I'm installing/removing things:

dpkg: warning: files list file for package 'chromium-codecs-ffmpeg-extra' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'unity-scope-chromiumbookmarks' missing; assuming package has no files currently installed

I have removed chromium and chrome, but I guess something left behind. What am I supposed to do to get rid of the dpkg: warning?

---

### Post by claracc on 2015-07-17
You can try to run in a x-term:

sudo apt-get autoremove

in order to delete packages which were automatically instaled and are not longer needed

---

### Post by sashhhh on 2015-07-19
I tried "autoremove", "autoclean" and "clean", but it's still there.

---

