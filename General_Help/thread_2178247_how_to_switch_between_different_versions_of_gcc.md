---
title: "how to switch between different versions of gcc"
date: 2013-10-02
forum: General Help
---

### Post by daiyue2 on 2013-10-02
Hi, I just start using Linux/Ubuntu, and I have installed gcc 3.3/3.4 along with g++ from PPA, and gcc 4.xx(default one I think) from Software Center. Now I wonder how to change the default compiler between them, say when I need gcc 3.3 instead of 4.xx to make/make install some pachage. Is there any command (or GUI) to do that and I am learning the commands to be honest.

cheers

---

### Post by TheFu on 2013-10-02
> **daiyue2 said:**
> Hi, I just start using Linux/Ubuntu, and I have installed gcc 3.3/3.4 along with g++ from PPA, and gcc 4.xx(default one I think) from Software Center. Now I wonder how to change the default compiler between them, say when I need gcc 3.3 instead of 4.xx to make/make install some pachage. Is there any command (or GUI) to do that and I am learning the commands to be honest.

cheers

When doing software development, you should control the entire environment 100% - compilers, core libraries, and local libraries.  That means you should avoid using the package manager version of these things.  This applies to all languages - python, perl, ruby, php, C/C++, java and others.  If you care about having specific versions of development tools, don't be tied to whatever the system repos provide. They are out for different end-goals than you are.

Perl has PerlBrew.
Ruby has RbEnv and RVM.

C/C++ might have something similar, but I've always managed it by setting a GCC_HOME and having all the bin/ lib/ inc/ directories under it based on the GCC_HOME environment.  That means you can have as many versions of these tools as you have storage to hold.  JAVA_HOME is a similar idea that is commonly used.  In the old days, setting a "tool"_HOME was a common way to control which was used.  Using symlinks was another when switching betewwn different tools didn't happen too often.

It also means that if there are security concerns for any part of the environment, then YOU are responsible for patches.

Does this make sense?

---

### Post by daiyue2 on 2013-10-03
> **TheFu said:**
> When doing software development, you should control the entire environment 100% - compilers, core libraries, and local libraries.  That means you should avoid using the package manager version of these things.  This applies to all languages - python, perl, ruby, php, C/C++, java and others.  If you care about having specific versions of development tools, don't be tied to whatever the system repos provide. They are out for different end-goals than you are.

Perl has PerlBrew.
Ruby has RbEnv and RVM.

C/C++ might have something similar, but I've always managed it by setting a GCC_HOME and having all the bin/ lib/ inc/ directories under it based on the GCC_HOME environment.  That means you can have as many versions of these tools as you have storage to hold.  JAVA_HOME is a similar idea that is commonly used.  In the old days, setting a "tool"_HOME was a common way to control which was used.  Using symlinks was another when switching betewwn different tools didn't happen too often.

It also means that if there are security concerns for any part of the environment, then YOU are responsible for patches.

Does this make sense?

Yes, thx for the reply. So how exactly can I set up GCC_HOME environment, where (location in the File System?) and how should I store these configurations (in a txt file?) and how these environment variables can be used during development (used in a command or modify the 'makevars' files), e.g., bulid/make packages. sry for the newbie questions coz I really don't know how linux works.

cheers

---

### Post by TheFu on 2013-10-03
> **daiyue2 said:**
> Yes, thx for the reply. So how exactly can I set up GCC_HOME environment, where (location in the File System?) and how should I store these configurations (in a txt file?) and how these environment variables can be used during development (used in a command or modify the 'makevars' files), e.g., bulid/make packages. sry for the newbie questions coz I really don't know how linux works.

cheers

This isn't a linux thing - this is a software development thing regardless of platform.
I think it would be best if you found a local - in-the-same-room - mentor. I wouldn't know where to begin for someone just starting out. Sorry.

There are lots of tools to know.  gmake will make your life easer. ddd for debugging, Plus all the language syntax and techniques.  I suppose there are online tutorials for this - have you looked for them?

When I learned, it was my full-time job and I was surrounded by UNIX software developers in a lab.  They already had projects setup so I could see them - I suggest you learn that same way - using examples.  There are thousands - perhaps millions - of examples online.  Any that involve using make and grabbing a tgz file with all the code should be good enough to start.

So after you figure out how to handle a program ... multiple versions of a program, do the same for GCC and the libraries. Same-Same. Not different.

---

