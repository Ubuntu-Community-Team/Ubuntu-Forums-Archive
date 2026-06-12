---
title: "amule upgrade"
date: 2006-12-02
forum: General Help
---

### Post by Corvair on 2006-12-02
I got a request to upgrade AMULE which I did
Since then I cannot laucnh AMULE anymore.

What went wrong?

I have Ubuntu version 6.06 LTS on an AMD Duron.

I tried launching it from a terminal and this is part of the 
message I got:

and your program used 2.6 (no debug,Unicode,compiler with C++ ABI 1002,wx contai ners,compatible with 2.4).
Aborted

---

### Post by lamego on 2006-12-02
Try:
Open a terminal:
sudo apt-get remove amule
sudo apt-get install amule

That should install you the "stable" version that is available on the repositories.

---

### Post by SilvioTO on 2006-12-02
same problem here, the error is:

Fatal Error: Mismatch between the program and library build versions detected.
The library used 2.6 (no debug,Unicode,compiler with C++ ABI 1002,wx containers),
and your program used 2.6 (no debug,Unicode,compiler with C++ ABI 1002,wx containers,compatible with 2.4).
Aborted

---

### Post by Corvair on 2006-12-02
Thanks for the suggestion but it still does not work. 
This is the result.

Fatal Error: Mismatch between the program and library build versions detected.
The library used 2.6 (no debug,Unicode,compiler with C++ ABI 1002,wx containers),
and your program used 2.6 (no debug,Unicode,compiler with C++ ABI 1002,wx containers,compatible with 2.4).
Aborted

---

### Post by Corvair on 2006-12-23
For anyone interrestsed or who had the same problem,
I went on aMule forum and found out that the problem was with wxGTK.

So I went to Synaptic and completely removed wxGTK.

Now I am able to launch aMule.

At first it would not connect so I loaded wxGTK from the site wxgtkwidget.org and installed it in tmp file.
Now everything seems to work fine.

---

