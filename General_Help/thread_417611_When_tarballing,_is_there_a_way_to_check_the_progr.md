---
title: "When tarballing, is there a way to check the progress?"
date: 2007-04-21
forum: General Help
---

### Post by rainwalker on 2007-04-21
I'm backing up my home directory before upgrading to Feisty, using the command 
```
sudo tar -cf home-20070421.tar .*
```
and I want to know how much is done/left. I've looked around and I can't find it anywhere, so I was hoping someone here could tell me.

---

### Post by mhansen on 2007-04-21
Well, you can see how much is done by going into that directory via another console and typing ls -l     That will give you the file size.  If you back up regularly, you know about how big the tarball will be, and about how long u have left.  That's the best I know of....



Regards,
Mike

---

### Post by rainwalker on 2007-04-21
Unfortunately, I don't back up regularly (I probably should, though)

---

### Post by mhansen on 2007-04-21
Well, u can also do a du -ms /directory to give u the size, in megabytes, of that directory.  Then, if you're doing just a straight tar (without compression), and do the ls -l I described in a previous post, you'll get an idea of how much you have left to tar.



Regards,
Mike

---

### Post by taurus on 2007-04-21
Put the option v for verbose in there and you can see the progress.

```
sudo tar -cvf home-20070421.tar .*
```

---

