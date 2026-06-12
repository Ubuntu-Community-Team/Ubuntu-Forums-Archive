---
title: "SVN load at bootup."
date: 2007-07-24
forum: General Help
---

### Post by netvampire on 2007-07-24
Hey,
basically when I load my computer I want SVN to automatically start up. Right now it does not do that, and I always have to use the terminal and type 'svnserve -d' to get it going .

I tried placed a file in the /etc/init.d/  folder that executed 'svnserve -d' but that did not work.

Does anyone have an Idea on how i can accomplish this.

Thanks

---

### Post by zanglang on 2007-07-24
Try:
> sudo update-rc.d <name of your svnserve script> defaults
That ought to set it up to run during bootup.

---

### Post by netvampire on 2007-07-24
Thanks i will try it when I get home from work.

---

### Post by netvampire on 2007-07-24
Thanks, that line worked great.

However, i did have to append an 's' to the word 'default'...... It should be 'defaults' for anyone who is experiencing the same problem.

---

### Post by zanglang on 2007-07-25
Ah, thanks for pointing that out. I should correct my post as well in case anyone comes along to read this. :D

---

