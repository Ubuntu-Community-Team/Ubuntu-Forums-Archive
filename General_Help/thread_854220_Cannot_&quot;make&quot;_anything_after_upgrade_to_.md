---
title: "Cannot &quot;make&quot; anything after upgrade to Hardy; no rule to make target"
date: 2008-07-09
forum: General Help
---

### Post by mhedges48 on 2008-07-09
Hello,
Since I've upgrade to Hardy, I cannot make anything. I have tried installing several things (madwifi and ndiswrapper for example) and always get the same error:

""
make[1]: Entering directory `/home/matt/My Documents/Code/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.24-19-generic M=/home/matt/My Documents/Code/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[2]: *** No rule to make target `Documents/Code/ndiswrapper-1.53/driver'.  Stop.
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/matt/My Documents/Code/ndiswrapper-1.53/driver'
make: *** [all] Error 2
""

I believe I have installed all necessary packages, and again I didn't have this problem in Feisty or in Gutsy.

Any ideas what the problem is?

many thanks
Matt

---

### Post by mhedges48 on 2008-07-13
I do not understand the logic of this, but I moved the installation folder to the Desktop, and did the Make, and it ran fine! It appears make will not run in folders with more than one word (I had tried to run it in My Documents)...

---

### Post by coffeecat on 2008-07-13
> **mhedges48 said:**
> I do not understand the logic of this

I wonder if it's the space in 'My Documents'. Spaces often cause problems in Unix, because the system starts looking for 'My' and thinks 'Documents' is an argument. Although I would have expected some sort of error message along those lines. Have you tried renaming My Documents to My_Documents? I know you don't need to but it might be interesting.

Alternatively you could completely ignore me. Even though I've run Gentoo for a couple of years, when it comes to compiling and all that stuff, I really don't know what I'm talking about. :lol:

---

