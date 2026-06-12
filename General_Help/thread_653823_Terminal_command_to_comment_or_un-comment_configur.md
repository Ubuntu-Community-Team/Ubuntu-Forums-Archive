---
title: "Terminal command to comment or un-comment configuration lines?"
date: 2007-12-30
forum: General Help
---

### Post by xelapond on 2007-12-30
Hello, 

Is there a terminal command that can comment out a line in a configuration file?  Then another one that will un-comment it?

Also, just deleting and putting it back in there would do fine.  Or for that matter, any way of disabling and re-enabling it.

Thanks

Alex

---

### Post by taurus on 2007-12-30
If you need to edit it, use nano.  And if it's system file, then include sudo in front.

```
sudo nano -Bw *filename*
```
Save the file with <Ctrl>o and exit with <Ctrl>x.

---

### Post by xelapond on 2007-12-30
Sorry for the confusion, I think I phrased that badly:^)

I mean comment or un-comment automatically, invisible to the user.  So a bash script could do it.

Thanks, 

Alex

---

