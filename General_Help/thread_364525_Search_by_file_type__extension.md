---
title: "Search by file type / extension?"
date: 2007-02-18
forum: General Help
---

### Post by fictivetoast on 2007-02-18
I've got a very simple problem that's driving me crazy:
How can I search for files of a certain type?

ex- I have .m4a files littered throughout my music collection, remnants from my old windows days, and i want to convert them - a task easily done with the handy soundconverter program.  BUT to do so, I need to find them all.  

Going to "search" in both nautilus and beagle, I get NO results when I try to look for *.m4a, 
.m4a, OR m4a !  How frustrating!  I guess it's just disregarding file extensions when it searches?  

I know this isn't hard, surely there's a way to comb a directory (and it's subdirectories) for certain file types, right?  Please help!  Thank you!

---

### Post by Peter76 on 2007-02-18
You can do it through the terminal:

locate *.m4a

---

### Post by Maestro23 on 2007-02-18
> **Peter76 said:**
> You can do it through the terminal:

locate *.m4a

Beat me to it.

---

### Post by akshaysrinivasan on 2007-02-18
You could do both simultaneously ,for example let us assume you have lame installed ,if you give the command 

abc@abc#find [directory] -name '*.m4a' -execdir lame '{}' \;

All your files will be converted to mp3 files.

---

### Post by fictivetoast on 2007-02-18
Wonderful, thank you!  What an immediate response!

---

### Post by akshaysrinivasan on 2007-02-18
You can find more about find by giving the command,

abc@abc##man find

It is one of the most helpful commands

---

### Post by cmertayak on 2007-02-18
> **fictivetoast said:**
> I've got a very simple problem that's driving me crazy:
How can I search for files of a certain type?

ex- I have .m4a files littered throughout my music collection, remnants from my old windows days, and i want to convert them - a task easily done with the handy soundconverter program.  BUT to do so, I need to find them all.  


try

```
sudo find / -iname *.m4a
```

If it won't work, make sure that all the devices that may contain the files that you're looking
are mounted properly.

---

