---
title: "Xubuntu 12.10 - how do I make an iso file from a DVD?"
date: 2012-12-09
forum: General Help
---

### Post by Carl H on 2012-12-09
Can't help thinking this is probably a bit of a dumb question, but...

I want to make an iso file from a DVD. I have previously used various versions of Ubuntu (and latterly, Mint) and in all  of those I could right-click on an optical disk in the file manager, select "Make a copy", and then choose "ISO file" as the target. 

I am now using Xubuntu 12.10 and cannot for the life of me work out how to do it! 

I tried XFBurn but it segfaults.

---

### Post by Cheesemill on 2012-12-09
I'm sure there are graphical applications that will do this but I  just use the command line:
```
dd if=/dev/sr0 of=filename.iso
```Where /dev/sr0 is your DVD drive, it can sometimes be called /dev/dvd or something similar, you can find out using the mount command

---

### Post by Carl H on 2012-12-09
Thank you. 

There was a time when dd would have been the first thing I'd have done without even thinking about using an application... :rolleyes:

For info (not sure if I should/need to report this as a bug?), XFBurn will run if started from the command line with sudo, otherwise it segfaults. This is on 64 bit.

---

