---
title: "Problem running a program, any ideas?"
date: 2007-02-10
forum: General Help
---

### Post by DaRush on 2007-02-10
I've encountered a problem that I have no idea how to even begin solving.

Alright, I'm running Ubuntu 6.10 X86_64 on my laptop, with a 2.6.19.1 kernel. I'm trying to install a screenwriting program called Celtx ([www.celtx.com)](www.celtx.com)).

After unpacking the tar.gz file (which is already compiled), instructions say to simply run run the "celtx" file from the new directory it created. When I attempt to do this, it gives me the following message:

(after typing ./celtx in the same directory)
./run-mozilla.sh: 424: ./celtx-bin: not found

Both of these files are present in the same directory.

(after trying to run this file with sh. run-mozilla.sh i get this message)
run-mozilla.sh: Cannot execute .

Being baffled by this I had my cousin attempt installing the same program (following the same two step process). His 32 bit Kubuntu ran it instantly. I've also attempted running this program the same way in my Fedora Core 6 X86_64 on my desktop, and after installing the 32 bit libraries It worked like a charm. I've installed the 32 bit libraries on my laptop as well, but this doesn't change anything - making me think there is a flaw somewhere else in my system - it simply does not want to run these files (keep in mind i've tried the same thing 5 times, including downloading the tar again and i know the files are good themselves).

I've also attempted to run this locally and as root, and that again changes nothing.

This makes me thing that there is a problem with the shell itself on my system, actually I don't even know what to think

If anyone can even point me in the right direction, it would be of help.

---

### Post by gradedcheese on 2007-02-10
just a guess, try it in bash: run "bash" and then continue trying to install.  If that helps, then replace the default shell (in 6.10 they use 'dash') with 'bash:

sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh

and then close any terminals that are open and open a new one...

---

### Post by DaRush on 2007-02-11
Thanks for the replies,

Problem is solved, I had to properly install the 32 bit libraries, and everything runs smoothly now...

---

