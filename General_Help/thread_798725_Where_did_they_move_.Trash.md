---
title: "Where did they move .Trash?"
date: 2008-05-18
forum: General Help
---

### Post by logos34 on 2008-05-18
.Trash used to be in /home/user.  What happened to it? 

I have a folder in it that I can't dump when I hit "empty trash" button in nautilus.  I need to change the permissions first.  Already tried as root (gksudo nautilus).  But I can't navigate to it in the terminal because it doesn't show up?  WTF?

help

---

### Post by TeoBigusGeekus on 2008-05-18
It's in
```
/home/username/.local/share/Trash/files
```

---

### Post by logos34 on 2008-05-18
> **TeoBigusGeekus said:**
> It's in
```
/home/username/.local/share/Trash/files
```

Thanks!

I wonder why they moved it?

---

### Post by TeoBigusGeekus on 2008-05-18
No idea mate... But they created a lot of trouble - if you do a search in the forums about the trash folder, you will see that, especially in the first week after Hardy's release, there was ~ one thread per couple of hours about it.

---

### Post by logos34 on 2008-05-18
I was lazy this time and didn't search.  

I wish the devs would leave well enough alone.  Seems to have caused a lot of unnecessary confusion

---

### Post by TeoBigusGeekus on 2008-05-18
> **logos34 said:**
> I was lazy this time and didn't search.  


:popcorn: Hey, don't apologize to a greek about laziness!!! :lolflag:

---

### Post by mahuyar on 2008-05-18
> **TeoBigusGeekus said:**
> It's in
```
/home/username/.local/share/Trash/files
```

They're just following the standards set by freedesktop.org.  You can read about the Trash-spec [here]("http://www.ramendik.ru/docs/trashspec.html").

OMG, can't believe we're talking so much about trash here... :lolflag:

---

### Post by fmonjaraz on 2008-05-19
Thanks for the info guys. I had the hardest time trying to delete to copied files from CD's (maps usa and SIMs 2).  Changing to the given directory and typing sudo rm -r (files), took care of it.

---

