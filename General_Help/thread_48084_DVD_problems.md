---
title: "DVD problems"
date: 2005-07-11
forum: General Help
---

### Post by paws on 2005-07-11
Hi,

I have no problem burning DVDs or reading data DVDs.

However, when I insert movie DVDs, almost always the DVD is not properly recognised. Ubuntu doesn't list it's contents and starts the application for CD/DVD recording, apparently mistaking it for an empty DVD. The fstab entry for the drive is the regular one.

Once, the contents were listed, but playback with Xine was totally garbled. Playback with MPlayer wouldn't work anyway because it's problems with AC3. Totem worked, but that's not a player I would like to use on a regular basis.

I already tried removing and reinstalling the CSS decryption and deleting the decss folder in the home directory where the keys are stored, but that didn't help.

Any ideas or suggestions?

---

### Post by rachii on 2005-07-11
im assuming you have libdvdcss2 package installed?
if not try that```
sudo apt-get install libdvdcss2
```

---

