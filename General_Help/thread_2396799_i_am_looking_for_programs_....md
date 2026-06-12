---
title: "i am looking for programs ..."
date: 2018-07-20
forum: General Help
---

### Post by Skaperen on 2018-07-20
i am looking for programs, preferably CLI commands, that can _convert between Unicode and UTF-8_ (i need each direction, but, as separate programs is OK).  i want input and output at least available in hexadecimal.  i want these as a quick means to calculate what the other code is when i have either the Unicode code point or the UTF-8 code sequence.  it would be preferred if these will function with the reserved surrogate pairs (used for coding large code points in UTF-16) so i can test if that is what is actually happening in some situations.

all i am finding from Google are versions of program that add support for these, add-ons to gain such, support, unicode fonts, and libraries for writing programs around Unicode and/or UTF-8.  a package scan has similar results.  maybe what i need is hidden away in there in a way i do not see.

---

### Post by Holger_Gehrke on 2018-07-21
You might want to take a look at GNU recode. The manual page for that program is a very bad joke, but it comes with a gnu info document that explains the use of the program (and the library it is an interface to) very well. 

Holger

---

### Post by Skaperen on 2018-07-21
yeah, the man page sure is a joke.  it is totally unclear how to give it even one Unicode code point to see what it should be in UTF-8. something intended specifically for Unicode/UTF-8 might be more helpful.  i've never understood how to use GNU info, either.

---

