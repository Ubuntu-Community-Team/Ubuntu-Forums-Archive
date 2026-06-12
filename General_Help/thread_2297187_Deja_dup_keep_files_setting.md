---
title: "Deja dup keep files setting"
date: 2015-10-01
forum: General Help
---

### Post by boris12 on 2015-10-01
Hello everyone ! 
I am new to Dejadup and I have just set it to back up all my "Data" partition which currently is around 300gb. I have set it to keep my files for at least 6 months. But going to dconf settings I see that it will make a full backup every 90 days. I just want to make an incremental backup of my files and not back it up every 3 months or so , as it is taking very long time and I think there will be minor changes to this , i.e. mostly documents , pictures updates. Not big files etc. 
How can I prevent this from doing so ?
Are there any special configuration I can set up?

Any help would be much appreciated ! 
Thank you in advance !

---

### Post by boris12 on 2015-10-03
Anyone please?

---

### Post by deadflowr on 2015-10-03
Do you want to set both the deletion period and the full-backup period to be the same?
Or do you want to disable the full-backup setting completely.

If the former try something like
```
 dconf write /org/gnome/deja-dup/full-backup-period "180"
```
this will set the full backup from 3 months(90 days) to 6 months (180 days)

or if you want to disable, perhaps set it to zero.
(I'm not sure about that, but it might work; I'm in no mood to try it, as  I like setting full backups periodically.)

Hope it helps

---

### Post by boris12 on 2015-10-04
My problem is that I am backing up large files . 300 gb twice seems a little bit overkill. What are your back up size ?

I really appreciate your reply!

---

