---
title: "Process using 100% cpu on 1 core only"
date: 2013-02-20
forum: General Help
---

### Post by UnknownFrequency on 2013-02-20
Hello there.

I recently decided to use Rhythmbox as my audio player. Suddently, I think while indexing files, it starts using 100% of only one core of my 
[I]Intel(R) Core(TM) i7-2675QM CPU @ 2.20GHz
MacBookPro 3.4.0-030400-generic x86_64 x86_64 x86_64 GNU/Linux[/I]
I tried this before, I think with Firefox. 

How do I tell Rhythmbox and other processes to divided their cpu usage to multiple cores?

---

### Post by dino99 on 2013-02-20
you simply cant  ;)

---

### Post by Impavidus on 2013-02-20
Some programs are designed to use multiple cores (the multithreaded programs), others are not. Indexing probably requires sorting in some way, which can gain from multithreading, but it appears rythmbox's devs didn't think it was important enough to implement multithreading for this.

---

### Post by JayKay3OOO on 2013-02-20
Mac

Parallels?

[http://askubuntu.com/questions/149428/why-does-parallels-7-have-such-poor-support-for-ubuntu-12-04](http://askubuntu.com/questions/149428/why-does-parallels-7-have-such-poor-support-for-ubuntu-12-04)

I'd guess you have to tell parallels to use all the cores. I know you can do this with virtualbox.

Otherwise it's rhythmbox, but I've always preferred Amarok or VLC.

---

### Post by Gyokuro on 2013-02-20
> **UnknownFrequency said:**
> Hello there.

I recently decided to use Rhythmbox as my audio player. Suddently, I think while indexing files, it starts using 100% of only one core of my 
[I]Intel(R) Core(TM) i7-2675QM CPU @ 2.20GHz
MacBookPro 3.4.0-030400-generic x86_64 x86_64 x86_64 GNU/Linux[/I]
I tried this before, I think with Firefox. 

How do I tell Rhythmbox and other processes to divided their cpu usage to multiple cores?

Hi

This is possible via cgroups - look here: [http://askubuntu.com/questions/94619/how-to-set-cpu-limit-for-given-process-permanently-cpulimit-and-nice-dont-work](http://askubuntu.com/questions/94619/how-to-set-cpu-limit-for-given-process-permanently-cpulimit-and-nice-dont-work)

---

### Post by sleash78 on 2013-02-20
press alt and f2, when it asks you what to run type the following:  gnome-terminal -x top

---

### Post by UnknownFrequency on 2013-02-20
cgroups works very well. Thanks for all the good answers

---

