---
title: "Nuke 9.08  crashing"
date: 2015-11-17
forum: General Help
---

### Post by RabbitWho on 2015-11-17
Nuke 9.08 non commercial I should say. It worked okay for a a few months, now whenever I try to track even a single frame it crashes. Suggestions for getting it to work? I tried swapping to Xubuntu because it is lighter but that didn't make a difference. Is there a way to find out exactly what's going wrong? I got it to crash while I had the system monitor opened and it didn't show any peak in ram or cpu usage. The program doesn't freeze up or anything, just disappears politely. 

...
    description: Notebook
    product: 80ES (LENOVO_BI_IDEAPAD9C_BU_idea_FM_Lenovo B50-30)

    version: Lenovo B50-30

    width: 64 bits
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU  N2840  @ 2.16GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Celeron(R) CPU  N2840  @ 2.16GHz
          slot: CPU 1
          size: 2172MHz
          capacity: 2172MHz
          width: 64 bits
          clock: 83MHz
          configuration: cores=2 enabledcores=2 threads=1
        *-cache:0
             description: L1 cache
             size: 32KiB
             capacity: 32KiB
        *-cache:1
             description: L2 cache
             size: 1MiB
             capacity: 1MiB
     *-cache
          description: L1 cache
          size: 24KiB
          capacity: 24KiB
     *-memory
          size: 4GiB

---

### Post by Geoffrey_Arndt on 2015-11-18
Perhaps the free trial expired?   Why not try Cheese . . . . which is popular in debian and ubuntu  ?    Also, have you checked "AlternativeTo" . . . . which allows you to search for similar software:   [http://alternativeto.net/](http://alternativeto.net/)

---

### Post by RabbitWho on 2015-11-18
It's not a free trial, it's a free (as in gratis) product. Cheese will not work. 1. I need to learn nuke for work 2. Cheese is not a fully featured node based professional digital composting software.. Cheese is an offline version of instagram with video capabilities 

If I am speaking double dutch: nuke is heavy. nuke isn't working. Help me get my heavy program working if you can, thanks :)



Edit: Doing one of these things fixed the problem, not sure which: 

1. Clicking on cache and then going to "clear all" < probably this
2. Going to edit > preferences > caching and adjusting the cache size (making it smaller)

---

### Post by Geoffrey_Arndt on 2015-11-18
Yes, thanks for the update . . . I see what Nuke can do . . . very impressive.   Glad you solved the problem and responded with the fix, as others may now benefit too.

Best Wishes

GGA

---

### Post by RabbitWho on 2015-11-19
Best wishes to you too and thanks for trying to help :) I'll go ahead and mark the thread as solved and hope, as you said, it helps others.

---

