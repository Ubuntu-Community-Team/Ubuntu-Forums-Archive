---
title: "Amarok + video Ipod problems, cant create lockfile"
date: 2007-07-05
forum: General Help
---

### Post by Digitallysick on 2007-07-05
I get this error

Media Device: failed to create lockfile on iPod mounted at /media/Adam’s iPod: Read-only file system

my ipod is in /media/Adam's iPod

how do i fix this??

---

### Post by Digitallysick on 2007-07-05
solution!

Fire up your mac, plug in your ipod and follow this

diskutil disableJournal /dev/diskXs3  where /dev/diskXs3 is the device assigned to the iPod. The "diskutil list" command shows you which device it in OS X the iPod is using. In my case, it was /dev/disk1s3.

this fixed it!

---

### Post by bonesdds on 2007-12-21
Bump

---

### Post by Trampis on 2008-05-25
Sorry to pull this thread of the back pages, but i thought it would be better to do that than make a new thread.

I have the same problem, but no mac to "fire up". I got this ipod from a freind who has named it "Moira's Classic ipod"

I tried chmod +w /media/ipod with no success (there is no /media/ipod it is /media/Moira's Classic Ipod)
so I do chmod +w /media/Moira's Classic iPod, with predictable results, the spaces in the name mess everything up.
```
chmod: cannot access `/media/Moiras Classic iPod\n\nchmod +w /media/Moiras': No such file or directory
chmod: cannot access `Classic': No such file or directory
chmod: cannot access `iPod': No such file or directory

```

I can't change the name, it is read only, Is there a way to get around this from my machine (only running hardy no partition)?

Edit: My iPod is not a iPod video, it is a first or second generation 20g. It has also been used exclusively on a Mac prior to this( i hear there is an issue with journaling?)

---

### Post by Trampis on 2008-05-25
bump + edit

---

### Post by Trampis on 2008-05-26
page 8 no response, I hate to do this but I am in a bind!

---

