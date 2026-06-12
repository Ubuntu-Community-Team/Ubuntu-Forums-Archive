---
title: "invalid ELF Header?"
date: 2007-05-29
forum: General Help
---

### Post by Limitlesschannels on 2007-05-29
what's an "invalid ELF Header" error? 

Just in case it helps to explain the situation, I have been trying to use LD_LIBRARY_PATH to implement some old glibc libraries for installing Sim City 3000.  

```
limitlesschannels@Compy:~/Desktop$ LD_LIBRARY_PATH=~/Desktop/Loki_Compat/ ~/Desktop/Loki_Compat/ld-linux.so.2 /media/cdrom0/setup.sh
/media/cdrom0/setup.sh: error while loading shared libraries: /media/cdrom0/setup.sh: invalid ELF header

```

---

### Post by mbradlcu on 2007-05-29
I've seen this error trying force using libs that were created on a different platform then the host machine. I"m not sure if this is the ELF we're talking about but here's the definition I found here:
[http://www.vistasource.com/vs2/pdf/elfusers.pdf](http://www.vistasource.com/vs2/pdf/elfusers.pdf)

Introducing ELF
          ELF (Extended Language Facility) is a powerful, flexible programming
          language that is bundled with Applixware. Using ELF, you can write
          simple macros that interact with your Applixware documents, or you
          can write complex, robust, stand-alone applications.
          ELF includes a library of almost 4000 macros, which allow you to
          control and manipulate every aspect of an Applixware document.
          Some macros allow you to interact with the underlying operating
          system, or mail your document to a co-worker in Tibet.

---

### Post by Limitlesschannels on 2007-05-29
heh, hmm..  Is there any ELF coders handy?

if you have seen this error before while forcing old libraries, can you tell me if my syntax is wrong or anything?

---

### Post by mbradlcu on 2007-05-29
I'm not sure about the syntax, specifically I've seen this error using the loki installer on my amd64 box. The fix was an installer switch to just extract the contents.. I'll post the specifics when I have access to that machine.

---

### Post by Stephen Howard on 2007-05-29
mbradlcu, no, that's not the ELF that produces the error.  ELF stands for "Executable and Linking Format" (or something close).  Its the file format used to store a unix executable file.

---

### Post by Limitlesschannels on 2007-05-31
So that would mean that according to my error the ELF exercutible file error would be due to an invalid setup.sh file off my cdrom?

---

