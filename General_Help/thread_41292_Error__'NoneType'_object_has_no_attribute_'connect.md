---
title: "Error:  'NoneType' object has no attribute 'connect'"
date: 2005-06-12
forum: General Help
---

### Post by monkotronic on 2005-06-12
trying to run pitivi on the latest ubuntu and get this error:

Error:  'NoneType' object has no attribute 'connect'

any ideas on what it might mean?

---

### Post by cwaldbieser on 2005-06-12
Sounds like a python runtime error.  I don't know what pitivi is, and I am not sure if you are interested in the technical aspects of the problem, but in case you can pass it on to one of the developers-- What the error means is that there was a variable (i.e. a name) that was bound to the special value 'None'.  Part of the program tried to access an attribute called 'connect' through this variable, but the 'None' value doesn't have this attribute.

This kind of error normally occurs in scenarios like this-- an argument is passed into a function, but somehow (usually neglecting to thoroughly check user input) the argument passed in did not conform to one or more types that were expected.

---

