---
title: "ksteak"
date: 2008-02-23
forum: General Help
---

### Post by mmertens on 2008-02-23
Good day Ubuntu Community!
I joined a pair of minutes ago and have a situation (not a deadly problem). I need a good off-line german-english dictionary. I couldn't put baby-trans to work. Before I left SuSE (because of its join with Novell that I felt a treason to the Linux community) I had Ksteak that worked very fine for my requirements. I downloaded the ksteak-1.0.0pre2.tar.bz2 file, but could not install it, what is a surprise for me, as I have the Kubuntu version and Ksteak belongs to the KDE project.

Somebody can tell me step by step how to install Ksteak and how to get the dictionaries to work? Maybe also for baby-trans that I think is the free version for the babylon dictionary.

Thank you in advance! Perhaps my questions and the possible solutions will be also useful to more people ...

Manfred

---

### Post by zvacet on 2008-02-24
```
tar jxvf ksteak-1.0.0pre2.tar.bz2
```

That will create directory.Go in that dir with cd command

cd /ksteak-1.0.0pre2

when you are inside you will see install file with instructions.In most cases is 

1. ./configure
2. make
3. sudo make install

---

