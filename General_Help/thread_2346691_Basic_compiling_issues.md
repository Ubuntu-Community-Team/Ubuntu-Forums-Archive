---
title: "Basic compiling issues"
date: 2016-12-17
forum: General Help
---

### Post by fedora-refugee2 on 2016-12-17
I wrote a simple "hello world" and it compiles with no errors but when I run it, I get errors saying ubuntu cannot find the files necessary to run type obj files. I am using Code::blocks with a gcc compiler. Any ideas? I made sure the obj file had execute permissions.

---

### Post by steeldriver on 2016-12-17
obj files aren't executables

What menu option are you selecting in code::blocks? what is the resulting gcc command that's being executed? You need to make sure you are **building **(i.e. compiling **and **linking) - not just compiling

---

### Post by TheFu on 2016-12-17
I've never used code:blocks.

.o files are relocatable objects. They haven't been "linked."
You need to link them. With 1 input file, it is common to compile AND link in 1 step.  If any .o file changes (because any .c file changed), then the program (no extension) needs to be recreated ... i.e. relinked.

$ gcc -c file.c  # creates .o files. 

BTW, this really belongs in the "software development" subforum.  Most people using Linux aren't developers.

---

### Post by fedora-refugee2 on 2016-12-18
I selected the build and run option. When I do, I get a message saying the program has not been built yet and asks if I want to build it. I click yes and am prompted to build it again. It must be something buggy in code::blocks.

---

### Post by TheFu on 2016-12-18
Is the storage being used a Linux file system? NTFS/FAT file systems are harder to use with Linux development. There are permissions settings which are expected.

For my first 2 yrs as a professional programmer, I assumed any issues that occurred were due to my lack of knowledge.  When I was still learning a language, it was always me, not the tools, with the issue.  I may have been using them incorrectly, but it was still my fault.

---

### Post by fedora-refugee2 on 2016-12-18
The linker options are not set. The guide I was using said just click build and run and it would work. I have to find a more reliable guide.

---

### Post by TheFu on 2016-12-18
> **fedora-refugee2 said:**
> The linker options are not set. The guide I was using said just click build and run and it would work. I have to find a more reliable guide.

This is one of the reasons I suggest learning to build software from a shell and doing that for a month or 2 before moving to any "environment."  Issues like this would be very clear then, since experience doing it the hard way would have paid off.

Plus understanding that many GUI programs really are just *program-option-creators* and call the same program used from a shell couldn't hurt.  For software development tools on Unix-like systems especially, this is how things are done.

AND finding a guide that is specific to the version of the tool on the same version of the OS that you are running could be helpful too.

---

### Post by fedora-refugee2 on 2016-12-20
> **TheFu said:**
> This is one of the reasons I suggest learning to build software from a shell and doing that for a month or 2 before moving to any "environment."  Issues like this would be very clear then, since experience doing it the hard way would have paid off.

Plus understanding that many GUI programs really are just *program-option-creators* and call the same program used from a shell couldn't hurt.  For software development tools on Unix-like systems especially, this is how things are done.

AND finding a guide that is specific to the version of the tool on the same version of the OS that you are running could be helpful too.
I would use the shell to compile but my brain is fried from building the computer. Thanks for the help.

---

