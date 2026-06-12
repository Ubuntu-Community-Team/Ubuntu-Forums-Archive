---
title: "Disk space allocation question (.ecryptfs) ?"
date: 2020-10-02
forum: General Help
---

### Post by tor30 on 2020-10-02
Hello,

I'm a bit surprised. What does that following mean? 
I think I have 40Gb data, but 80Gb are used?


(base) andi@pc1:/home$ sudo du -h -d 1 /home/
40G    /home/andi
40G    /home/.ecryptfs
80G    /home/

(base) andi@pc1:/home$ sudo du  -d 1 /home/
41481524    /home/andi
41481548    /home/.ecryptfs
82963076    /home/

(base) andi@pc1:/home$ df | grep home
/home/andi/.Private      93605824   78767204   10119924   89% /home/andi

(base) andi@ThinkPadT460s:/home$ du -sh /home/andi/
40G    /home/andi/

---

### Post by dinkidonk on 2020-10-02
It would be obvious to assume that /home/ uses the space of its sub-directories (andi + .ecryptfs).

EDIT: I think I misunderstood the question.. Since your home folder is encrypted, then the contents is actually stored in "/home/.ecryptfs/andi" and the content is then mounted to "/home/andi" when unlocked. That means that "/home/andi" points to data in "/home/.ecryptfs", so the sum of 80G is actually two times the same 40G. Misleading it is, however.. ;-)

---

