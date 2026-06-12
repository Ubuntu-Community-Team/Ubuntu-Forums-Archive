---
title: "Is it possible to compile win32 binaries using GCC?"
date: 2006-11-04
forum: General Help
---

### Post by dr_d on 2006-11-04
is it possible to tell gcc compile to the portable executable format so that the code will run under windows? would gcc be able to resolve the addresses for win32 api function calls?

i'm asking this because i'm sick of having to install my windows compiler from 5 separate cd's every time.

---

### Post by boban on 2006-11-04
I don't think that gcc is not capable of creating "portable executable". For that you should try java (or maybe c#)

But - there is a way for compiling code (with only minor changes if you have writen code with portability in mind) with gcc under windows - check mingw ([http://www.mingw.org/](http://www.mingw.org/)) and cygwin ([http://www.cygwin.com/)](http://www.cygwin.com/)).

---

### Post by dr_d on 2006-11-04
oh too bad...

it's not that i've specifically written code with portability in mind, just that i was trying to do away with having a C compiler on my windows partition...

i'm surprised to hear that gcc can't compile to the PE format -- but in any event i didn't expect it to be able to resolve win32 api function addresses.

as for java and c# i've had to learn both of those (stupid uni degree) and i know first hand that i'd prefer a swift kick into the stomach anyday :)



anyway thanks for the info...

cheers.

---

