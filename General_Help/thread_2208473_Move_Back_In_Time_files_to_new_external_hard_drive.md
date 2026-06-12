---
title: "Move Back In Time files to new external hard drive"
date: 2014-02-28
forum: General Help
---

### Post by jolindbe on 2014-02-28
Hi!

I'm replacing my old external hard drive with a new bigger one, and I'd like to move my [Back In Time]("http://backintime.le-web.org/") backups to the new one. If it helps, Back In Time is just a front-end to rsync.
So I've tried to just copy-paste the directory in Nautilus, or to cp the files through the terminal, but in both cases I end up with running out of disk space, since the new folder grows much, much bigger than the original. I am guessing this has to do with the structure of rsync directories with links everywhere... is there any way I can get around this?
I've tried to google this for a while, but for weird reasons, google seems to replace "Back In Time" hits with "Time Machine" (for mac) hits, so it is difficult to find useful info on this.

Thanks for any help!

---

### Post by lukeiamyourfather on 2014-02-28
If you use rsync with the option to copy links as links it should work just fine. I'm guess when you're duplicating the files it's copying the files the links are pointing to instead of the links. Something like this should do the trick.

```
rsync -a /olddisk/files/ /newdisk/files/
```

The specific option for copying links as links is -l but -a also includes that option.

---

### Post by lukeiamyourfather on 2014-02-28
One more thing, the -l is for copying symbolic links. They might be hard links in which case you'd want to use -H to copy hard links. See the rsync manual for more info on that.

```
man rsync
```

---

