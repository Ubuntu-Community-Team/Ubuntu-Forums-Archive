---
title: "help understanding mingw"
date: 2008-02-24
forum: General Help
---

### Post by NullHead on 2008-02-24
I'm thinking of trying to port [BMPx]("http://bmpx.backtrace.info/") to windows using the source code provided on the website using mingw. 

Can I simply configure, make it and than use mingw to produce a exe? or am I just being delusional ?

Is this possible or not?

---

### Post by NullHead on 2008-02-24
Anyone have any speculations about this? Even any thoughts? 

BUMP

---

### Post by danwood76 on 2008-02-24
you would need to modify a load of the code depending on which graphical framework the original app is built on.
Plus you would also need all the background programs and dependencies for the app to work properly.

It is a lot of work porting an application from one OS to the other unless it was written with really modular code that can easily be adapted.

---

### Post by NullHead on 2008-02-24
Hmm I see your pointe there. 

It's written to use gtk and I would have to change allot of stuff to get it to work properly ... does this mean mingw is for windows programmers using linux as there programing environment?

---

### Post by danwood76 on 2008-02-25
It is possible to write code that is compatible with both operating systems.
In my first year at uni I had to write some command line programs that would compile under gcc.
I used mingw then (before my days using linux fully) and was able to write code fully compliant with both systems.

The problem is when you start using graphical APIs.
I had a look at the BMPx site and it seems it uses gstreamer as a backend to play audio so you would also need to port the audio playing side to a similar win32 program.

---

### Post by NullHead on 2008-02-25
I am now seeing flaws in my plans! 

Thanks for your thoughts, NullHead.

---

