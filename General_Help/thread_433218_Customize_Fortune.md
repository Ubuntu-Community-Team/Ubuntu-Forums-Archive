---
title: "Customize Fortune"
date: 2007-05-04
forum: General Help
---

### Post by andycyca on 2007-05-04
Hi everyone!

WARNING: I'm a Linux N00b

Last night I was playing with XScreensaver in my Xubuntu and found about this program called **Fortune** which displays small phrases and such. Obviously, I wanted to customize it. I found a folder (i can't remember the exact path) with several txt and dat files that contained the phrases. I tried changing some but later Fortune kept giving me errorrs, so I swithed it back the way it was.

So, I'm looking for a way to customize Fortune. **How can I add/remove/replace the default phrases?** 

Thanks!

---

### Post by lloyd_b on 2007-05-05
I'm assuming the files you found were out in "/usr/share/games/fortunes". 

To make changes to these files:

1.  Edit the base file (i.e "fortunes", "literature", etc), adding/deleting fortunes.  Note that a line with a single "%" acts as a separator between fortunes.  These files are typically owned by "root", so you'll need to use sudo/gksudo with your editor.

2.  Run the program "strfile" to rebuild the associated ".dat" file.  In a terminal window:
```
cd /usr/share/games/fortunes
sudo strfile fortunes
```

Lloyd B.

---

### Post by andycyca on 2007-05-05
Thanks Lloyd! I'm gonna try it and I'll post later!

---

