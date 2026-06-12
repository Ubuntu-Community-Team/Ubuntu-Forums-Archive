---
title: "Fortran"
date: 2016-08-11
forum: General Help
---

### Post by george110 on 2016-08-11
I noticed just this week that one of the updates contained a fortran compiler.
Is this naturally a part of Ubuntu's OS which was being updated or is it it fact something new that now allows us to programme in Fortran without any hassles ?
No provisions for the simpler qbasic as yet. Can only hope but still access to Fortran would be an enormous advantage.

---

### Post by QIII on 2016-08-11
GNU compilers for Fortran 77 and Fortran 95 (at least) have been available in the repos for a long time.

You may have recently installed something that brought one of the compilers in as a dependency without knowing it.

---

### Post by Topsiho on 2016-08-11
I agree with QIII.

Qbasic is a closed source Microsoft product, which was (or is?) delivered together with Windows, so little chance to find this in the repositories of a Linux open source distribution :)

Topsiho

---

### Post by lisati on 2016-08-11
If you're looking for a version of BASIC, there are options. I've used "FreeBasic" in the past on both Ubuntu and Windows.

---

### Post by george110 on 2016-08-11
How & from where do you get " free basic " onto Ubuntu ? 
Is it that similar to gwbasic or qbasic ? As importantly are there memory restrictions to less than 32kb 's ?  If not what is the memory allocation. Would it be similar to Fortran's ?

---

### Post by coldraven on 2016-08-11
Try searching for answers before asking multiple questions. It took me 10 seconds to find this:
[https://en.wikipedia.org/wiki/FreeBASIC](https://en.wikipedia.org/wiki/FreeBASIC)

---

### Post by lisati on 2016-08-11
Also look in the Software Centre (also known as "Ubuntu Software").

---

### Post by Topsiho on 2016-08-11
You could also try running qbasic in dosbox, which is a dos-emulator, and in the repositories.
I can understand that you prefer using qbasic, if you already know it, and have documentation (read: a book, or else) for it.

Topsiho

---

### Post by george110 on 2016-08-11
There's no Fortran in the software centre nor can you Q it with any results.

---

### Post by george110 on 2016-08-11
How would I get qbasic into dosbox. 
Would I download qbasic from the web & then try to open it in dosbox ?

---

### Post by mook765 on 2016-08-11
In the Synaptic Package Manager you will find a lot about Fortran

---

### Post by george110 on 2016-08-11
Very helpful ! Never programmed in Fortran eh ?

---

### Post by lisati on 2016-08-12
All this talk of Fortran takes me back to my school days, it was the first language I recall trying. It has been a LONG time, decades in fact.

The version of Fortran I've briefly looked at on Ubuntu some years ago was command-line based. I can't recall how I installed it.

---

### Post by sudodus on 2016-08-13
Long ago I used to program in fortran. For sentimental reasons I have installed ***gfortran***, but I have not really tested it.

```
sudo apt-get install gfortran
```

It is version 4:5.3.1-1ubuntu1, which comes with *ubuntu 16.04.1 LTS. And as described by *lisati*, it is command-line based.

From ```
man gfortran
```

```
       -std=std
           Specify the standard to which the program is expected to conform,
           which may be one of f95, f2003, f2008, gnu, or legacy.  The default
           value for std is gnu, which specifies a superset of the Fortran 95
           standard that includes all of the extensions supported by GNU
           Fortran, although warnings will be given for obsolete extensions
           not recommended for use in new code.  The legacy value is
           equivalent but without the warnings for obsolete extensions, and
           may be useful for old non-standard programs.  The f95, f2003 and
           f2008 values specify strict conformance to the Fortran 95, Fortran
           2003 and Fortran 2008 standards, respectively; errors are given for
           all extensions beyond the relevant language standard, and warnings
           are given for the Fortran 77 features that are permitted but
           obsolescent in later standards. -std=f2008ts allows the Fortran
           2008 standard including the additions of the Technical
           Specification (TS) 29113 on Further Interoperability of Fortran
           with C and TS 18508 on Additional Parallel Features in Fortran.
```

you can see which versions of fortran that are implemented.

---

