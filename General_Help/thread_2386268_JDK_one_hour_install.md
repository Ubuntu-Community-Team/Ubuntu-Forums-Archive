---
title: "JDK one hour install"
date: 2018-03-03
forum: General Help
---

### Post by redy2 on 2018-03-03
Hi all,

I am new to Linux ubuntu .
I am installing JDK (java development kit) and after 10 minutes it only got to like 10% on the progress bar . It is still progressing slowly and the laptop is a decent i5 8250U 8 threaded .

My question is if it is normal or if there are stuff that are normal to take so long on linux cause i find it weird. On windows it took only 2 or 3 minutes . 

Thanks
Adrian

---

### Post by ubname on 2018-03-03
slow download probably...

---

### Post by monkeybrain20122 on 2018-03-03
> **redy2 said:**
> Hi all,

I am new to Linux ubuntu .
I am installing JDK (java development kit) and after 10 minutes it only got to like 10% on the progress bar . It is still progressing slowly and the laptop is a decent i5 8250U 8 threaded .

My question is if it is normal or if there are stuff that are normal to take so long on linux cause i find it weird. On windows it took only 2 or 3 minutes . 

Thanks
Adrian

Not in Linux, only on your machine. Took me about a minute or less. :)

---

### Post by The Cog on 2018-03-03
I would think either the download is slow, or (much worse) you are having I/O errors with the hard disk. If you install with apt on the command line you can see when it finishes downloading and begins unpacking. My PC went like that a year or so ago. Eventually a replacement disk made the whole machine very fast again. But the problem is definitely something to do with your end. Having 8 threads won't help. If it's the install phase rather than the download, I think the limit is disk I/O and not processing power.

---

### Post by redy2 on 2018-03-03
2 hours have passed and it only finnished 1/3 of the install xD 
It helps a great deal to know the issue is on my end . thank you all million !

---

### Post by speartip on 2018-03-03
2 Questions to ask here:
1. What are your normal download speeds? &
2. Are you installing JDK from the official Ubuntu Repos, where I think it's called "icedtea-plugin" or are you installing from somewhere else?

---

