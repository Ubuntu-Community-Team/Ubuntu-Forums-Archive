---
title: "us.archive.ubuntu.com down again"
date: 2006-08-06
forum: General Help
---

### Post by jordanm on 2006-08-06
I can't use apt to update cause this mirror is down again. I work as a Sys tem Analyst, but I dont know how the Ubuntu team expects people like me to recommend ubuntu for commercial applications when they cant even keep a mirror with high uptime. Good thing I only use Ubuntu at home.

---

### Post by Arisna on 2006-08-06
There are lots of mirrors available.  If you were using us.archive.ubuntu.com, the next one you'd probably want to try would be archive.ubuntu.com, which I believe is in the UK.  It is possible to switch relatively easily using :%s/us\.archive/archive/g as a command in Vim on the file /etc/apt/sources.list

---

### Post by pppetter on 2006-08-06
That, of course, isn't something good. But it seems like it's up again anyways, so it wasn't really that much trouble? And may I add, it's not the ubuntucommunity to blaim when the us mirror is down, but Argonne National Laboratory.

---

### Post by jordanm on 2006-08-07
This is all true. I guess its just frustration since I know that Ubuntu is by far the best distribution, yet small things like this keep happening which seem like they may prevent some of its commercial usability.

---

### Post by tommcd on 2006-08-07
> **Arisna said:**
> There are lots of mirrors available.  If you were using us.archive.ubuntu.com, the next one you'd probably want to try would be archive.ubuntu.com, which I believe is in the UK.  It is possible to switch relatively easily using :%s/us\.archive/archive/g as a command in Vim on the file /etc/apt/sources.list

How exactly do you do that? Could you give an example please? I too have had this problem.

---

### Post by Christmas on 2006-08-07
For me the security repository was down in some occasions but I always commented it out and updated the rest. Just use another mirror temporary, even it's slower.

---

### Post by pppetter on 2006-08-07
And I would just wait for it to go up again...it doesn't take THAT long.

Although my mirror (se), has _never_ been down...kinda strange that the US one does, I don't think that ANL's a bunch of noobs :P

---

