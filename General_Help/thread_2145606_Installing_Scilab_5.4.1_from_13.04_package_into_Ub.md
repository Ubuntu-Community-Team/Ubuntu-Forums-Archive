---
title: "Installing Scilab 5.4.1 from 13.04 package into Ubuntu 12.04"
date: 2013-05-15
forum: General Help
---

### Post by zemega on 2013-05-15
How can I do this? The latest stable package of Scilab is availabe to 13.04, while 12.04 still has the old package. So I want to install 5.4.1 from the 13.04 package into Ubuntu 12.04. Should I hunt down the debian package from 13.04 and install it manually into 12.04?

---

### Post by ibjsb4 on 2013-05-15
Have you tried the Scilab home page?

---

### Post by zemega on 2013-05-15
I have. There are also latest binary there that can be run inside 12.04, but it has a critical bug in it to me. I can't export plots I created correctly. Creating and saving plots is an important step in my work. I have reported the bugs. Compiling from source is also bad, because some of the dependacies requires me to uninstall some of the libraries from other needed programs, it would render the program 'broken'. I understand that this bug is fixed when installing Scilab 5.4.1 in 13.04 using the software manager. While I personally run 13.04, the main computer at my lab runs 12.04 and is much more powerful than my laptop.

---

### Post by HermanAB on 2013-05-16
I would rather download the Scilab source and compile it.  That way, it is guaranteed to work on your older system.

---

### Post by zemega on 2013-05-16
That would make some programs in a shared 12.04 broke. I can't do that.

---

### Post by zemega on 2013-05-17
Bump

---

### Post by oldrocker99 on 2013-05-17
> **zemega said:**
> That would make some programs in a shared 12.04 broke. I can't do that.

How, exacttly? Compiling a program on your own system should make it work perfectly, and what are you worried about breaking?

---

### Post by zemega on 2013-05-18
It ask to uninstall some lib used by other programs. I tried once before compiling on source, and uninstall some libs. The other programs would not run unless i install the libs back, which in turn cause scilab not to run instead. And the other programs are used by many people.

---

