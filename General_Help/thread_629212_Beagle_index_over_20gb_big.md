---
title: "Beagle index over 20gb big?"
date: 2007-12-02
forum: General Help
---

### Post by Skerit on 2007-12-02
My current .beagle map is *gasp* 20 gigabytes big ...

I know I have a lot of files, my total HD capacity is a terabyte, but still! 

Is this normal, or should I just tell it to ignore too small files? (Like, say, .so's and wine's .dll's ...)

---

### Post by posterboy on 2007-12-02
Wow! That IS big! Did you turn on extended attributes? That has an enormous effect on both speed and size of the database. Also, as you likely know already, anything that begins with a dot is ignored, so I keep my source code for things I have compiled in .src, to prevent them being indexed. This can be done anywhere you like. Maybe help to cut it down a bit.

---

### Post by Skerit on 2007-12-02
Ahh, but mine does index the hidden folders...

I thought it did so on everyone's computer, how else could it search through Pidgin's chatlogs? And even if I wanted to deactivate it, I have no idea where that option is..

Does beagle clean out old index files? Because, the past year, my files moved around *a lot* (different mountnames and such...)

Now that I think of it, my beagle has been acting strangely.. Even though beagle is in my startup from time to time, when I look for something, it says the service isn't activated...

---

### Post by posterboy on 2007-12-02
Not really, it _should_ skip all the dot files. Now, the thing is coded so that stuff like dot evolution, dot pidgin etc. are exempted from this rule, else it wouldn't work at all on email, etc. There's also a way to set up other rules for it, using beagle-settings, and although I have never used it, I think that has a graphical counterpart. You can force both inclusions and exclusions using this. You might want to try blowing away your index, Simply done, just rm -rf .beagle, and let him start over with your rules. I learned a lot by tailing .beagle/Log/current-Beagle. Also, type beagle and 2 tabs, he has a lot of ways to  see what he's doing. Helpful to start beagle with beagled --debug, to get information from his log.

---

### Post by dbera on 2007-12-02
> **Skerit said:**
> My current .beagle map is *gasp* 20 gigabytes big ...
I know I have a lot of files, my total HD capacity is a terabyte, but still! 
Is this normal, or should I just tell it to ignore too small files? (Like, say, .so's and wine's .dll's ...)

Nops ... this is not normal. I can bet that your HOME/.beagle/Log directory is taking up all the space. You can safely delete that directory and then restart beagle to reclaim the space. However, the huge log directory is an indication of some other bug. Several of them were fixed in 0.2.18, one particular one with respect to Evolution mail indexing was fixed just after 0.2.18 so didnt make it to gutsy. That could be one of the problems. And a number of different problems were fixed in the latest 0.3.0 but who knows if that will ever be backported to gutsy.

---

