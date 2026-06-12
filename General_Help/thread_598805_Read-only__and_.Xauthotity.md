---
title: "Read-only / and .Xauthotity"
date: 2007-10-31
forum: General Help
---

### Post by steve0921 on 2007-10-31
I've been working on a few embedded systems lately and it's been decided that it would be nice if their root file systems were read-only (mostly because of the chance of sudden power cycling, and journalling has been disabled to go easy on the flash drive).

Now, this has worked fine except on one system which can run some simple Qt apps over ssh. When I log in with ssh -X, I see the error message: ```
/usr/bin/xauth:  error in locking authority file /home/steve/.Xauthority
```
I've tried to make .Xauthority a link to a file in a tmpfs folder so that it can be written, but this doesn't appear to fix anything. What is required of the file in order for xauth to lock it? Does it need to be able to delete and recreate the file?

Are there any clever ways around this problem?

---

