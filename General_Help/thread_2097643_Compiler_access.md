---
title: "Compiler access"
date: 2012-12-23
forum: General Help
---

### Post by briermay on 2012-12-23
hello I've search Google and the only thing that keeps coming up is how to do this with cpanel. Well I don't run Cpanel as I have designed my own control panel for hosting but I need to set it so that only certain user group has access to compile programs. for example full shell users would need to compile things but a web hosting account may like shell access but I don't want them to compile things. I know this is possible because cpanel is capable of doing it but I need to know how to implement it without cpanel.
 
Thank you

---

### Post by rnerwein on 2012-12-24
> **briermay said:**
> hello I've search Google and the only thing that keeps coming up is how to do this with cpanel. Well I don't run Cpanel as I have designed my own control panel for hosting but I need to set it so that only certain user group has access to compile programs. for example full shell users would need to compile things but a web hosting account may like shell access but I don't want them to compile things. I know this is possible because cpanel is capable of doing it but I need to know how to implement it without cpanel.
 
Thank you
hi
create a group, lets say compile and add those users who are allowed to compile in this group too. chmod the the compiler that it got only for the owner and that group permission to execute.
cheers

---

### Post by briermay on 2012-12-24
ok that's what I was thinking, but which files need that done ? I know gcc and cc any other files ?

---

### Post by MG&amp;TL on 2012-12-24
> **briermay said:**
> ok that's what I was thinking, but which files need that done ? I know gcc and cc any other files ?

Depends which compilers you want to block, but that would cripple the C compiler for anyone trying to use it, yes.

---

### Post by briermay on 2012-12-24
I want to block access to *ALL* compilers but don't know which files I need to set

---

### Post by MG&amp;TL on 2012-12-24
> **briermay said:**
> I want to block access to *ALL* compilers but don't know which files I need to set

Which ones do you have installed? Does "compiler" include interpreters as well, like perl or python?

---

