---
title: "Update Problems"
date: 2013-01-12
forum: General Help
---

### Post by bman on 2013-01-12
I just checked for updates and there was 2 items that I couldn't select. Both were related to VLC.

I then did a partial update, which I was not sure what it was, but it removed VLC from the system as well as xscreensaver.

I have no idea what just happened lol

Any ideas?

---

### Post by TheFu on 2013-01-12
> **bman said:**
> I just checked for updates and there was 2 items that I couldn't select. Both were related to VLC.

I then did a partial update, which I was not sure what it was, but it removed VLC from the system as well as xscreensaver.

I have no idea what just happened lol

Any ideas?

Your description isn't helping me come up with an answer. Sorry.

I do updates from the CLI, so that any warnings and errors can easily be copy/pasted into the forums. Perhaps that would help?

I did see that VLC was updated this week.

```
$ sudo apt-get update
$ sudo apt-get dist-upgrade | tee /tmp/dupgr.log
```
is all you need. This will replace kernels for your current distribution with newer versions. It will never upgrade from 1 dist to another. There is a different command for that.

---

### Post by bman on 2013-01-12
I don't know why it didn't explain it in the update, but I guess that is what happened.

I went from 12.04 to 12.04.1. And for some reason it removed those 2 things.

---

### Post by ibjsb4 on 2013-01-13
Partial upgrades

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

---

