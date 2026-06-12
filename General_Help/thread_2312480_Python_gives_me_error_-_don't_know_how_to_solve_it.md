---
title: "Python gives me error - don't know how to solve it"
date: 2016-02-04
forum: General Help
---

### Post by mparalovos on 2016-02-04
Hello Everyone,

I just moved back to ubuntu 14.04 after being on windows 10.   

I'm trying to run a python script in the directory.  I have not done anything fancy to install python and can access the interactive shell with no problem, but when i run the script i get this response:

> python markthing.pyTraceback (most recent call last):
  File "markthing.py", line 18, in <module>
    from pdfminer.converter import TextConverter
ImportError: No module named pdfminer.converter




I have tried googling it and i just don't get a good path to find the right answer. Any direction on how to solve this problem would be greatly appreciated! 

This script worked flawlessly on my windows 10 computer.  Same script, but i don't understand the error and i can't find a path to fix it by googling it. 

After doing a bit more research - this script may be written in python 2.7 instead of 3.4.  How would i check?  Hmm...more googling.  

Thanks!

---

### Post by oldos2er on 2016-02-04
It's probably looking for python-pdfminer; do you have that package installed? Which version of Ubuntu are you running?

---

### Post by mparalovos on 2016-02-04
14.04 lts.  Could i just install that package through synaptic? (i'll look, i'm on my win 10 machine right now).

---

### Post by oldos2er on 2016-02-04
I assume so. I'm running 15.10 so I can't verify that for you.

---

