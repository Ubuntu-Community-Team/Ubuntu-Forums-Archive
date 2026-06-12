---
title: "How to stop hibernate increasing swap usage?"
date: 2008-03-25
forum: General Help
---

### Post by gen0 on 2008-03-25
I have an old Toshiba laptop with 256mb RAM on which I run XUbuntu 7.10.  I Hibernate/Resume it frequently as it is used on the train to/from work, and I find that each time I do this, a little more of my physical RAM gets paged out to the swap partition making my machine less and less responsive each time.  This is despite me having plenty of physical RAM free.  This is not something that happens under Windows.  I'm wondering is this something that I can change via configuration?  Or is it a result of Linux using the same swap partition for both virtual-memory and hibernation (as opposed to Windows' separate virtual-memory and hibernation files)??

Here's some sample output from 'free' taken immediately before and after a Hibernate/Resume to illustrate the point:

```
$ #Before Hibernate
$ free
             total       used       free     shared    buffers     cached
Mem:        239072     217508      21564          0       4516      96588
-/+ buffers/cache:     116404     122668
Swap:       481908      51288     430620
$ #After Hibernate/Resume
$ free
             total       used       free     shared    buffers     cached
Mem:        239072     118440     120632          0        704      36472
-/+ buffers/cache:      81264     157808
Swap:       481908      78876     403032

```
As you can see, simply hibernating the machine resulted in nearly 30MB of data moving to my Swap partition from Physical RAM.

I have swappiness set to 0:

```
$ sudo sysctl vm.swappiness
vm.swappiness = 0
```

and I've tried using the standard Ubuntu Hibernate (by selecting Quit -> Hibernate via the GUI) or s2disk from the command-line.

---

### Post by LaRoza on 2008-03-25
They are probably different files, just in the Swap partition.

Could you get a bigger swap partition?

(The Windows hiberfil.sys will eat up your hard drive space in the C: drive, so their way isn't better.)

---

### Post by gen0 on 2008-03-25
Thanks for your suggestion.  I could try to increase the swap partition size to say 512MB, though I'm not convinced this would help - in the above example the swap partition is more than big enough for my currently used swap + 256mb RAM.

---

