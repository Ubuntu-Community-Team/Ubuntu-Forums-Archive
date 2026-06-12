---
title: "Problems with g++"
date: 2007-07-03
forum: General Help
---

### Post by gotak on 2007-07-03
I get this when i try to run g++:

/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cstdlib:135: error: ‘::system’ has not been declared

It seems to be a problem with either something missing or something in their file but I can't figure out what.

---

### Post by JerryK on 2007-07-03
Is this your own application or a standard Linux application?  If it is your own, can you post the source code that is causing the error?
Jerry

---

### Post by gotak on 2007-07-12
Well i found a fix which is to comment out ::system on line 114 in cstdlib. However, that seems like it's going to cause other problems.

Also I had to switch back to gcc 3.3 because somehow there were more issues with 4.1.2 in regards to fstream and using that for file IO.

What's going on with ubuntu these errors seems very strange.

---

### Post by bashologist on 2007-07-12
Is the "::" thing new to c++? I think it's called "member" something. Maybe it's treating the file as c and not c++.

---

### Post by gotak on 2007-07-12
Well yes I know what it is the problem is that you have to comment it out to make things work. Happened with gcc 3.3 and associated libs as well. But at least 3.3 doesn't seg fault on doing file IO with fstream.

This is annoying.

---

