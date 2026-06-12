---
title: "help sync /usr folder ubuntu pc1 with pc2"
date: 2008-05-29
forum: General Help
---

### Post by oscar_19 on 2008-05-29
I have to sync one ubuntu pc1 with other ubuntu pc2
I need to sync all the / but I try to make it but some folders its better don't make it.
I only sync /etc /var /home and I try to sync the programs that are in /usr becauuse I would like to have  my web server and my server sycronised and the programs thta I have in pc1 I would like to have in pc2. Do you know how to make it?

---

### Post by brownicb on 2008-05-29
From pc2, run:

rsync -av pc1:/source/dir/* /target/dir

---

### Post by oscar_19 on 2008-05-29
Imake it but I have to make with the sudo rsync to aoid permission denied (13) but some programs don't sync.

---

### Post by ilrudie on 2008-05-29
Are the "programs" that aren't syncing soft links?  They may link to another file that isn't being synced.  Can you be more specific by what you mean when you say they don't sync?  Are the files not there?  They are there but the programs don't run?

---

