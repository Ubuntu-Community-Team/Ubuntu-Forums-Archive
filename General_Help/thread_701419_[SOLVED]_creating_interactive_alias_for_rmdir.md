---
title: "[SOLVED] creating interactive alias for rmdir???"
date: 2008-02-19
forum: General Help
---

### Post by seventhc on 2008-02-19
I have set up a few different aliases in my .bashrc but I would like to have something similar to the interactive option (-i).
Unfortunately -i is not an option with rmdir, I have read the man pages on it and it isn't mentioned at all. It works with rm but not with rmdir, is there any way to have this feature?
I want it b/c I sometimes I create test directories or temporary directories and for safety reasons would like it to ask me if I'm sure and then answer with a 'y'.
Thanks :)

---

### Post by y-lee on 2008-02-19
The only thing I can think of is to try to write your own shell script for that or a program to do that in a language such as perl or python.

---

### Post by seventhc on 2008-02-19
Thanks for the reply. :)
How would that work with the .bashrc? I can't run a python script from within the bashrc?
Can I?

---

### Post by pointone on 2008-02-19
```
alias rmdir='/path/to/your/script'
```

```
#! /usr/bin/env python

import sys, os

response = raw_input("Are you sure you want to remove the directory '%s'? " % sys.argv[1])
if response.lower() in ["y", "ye", "yes"]:
    command = " ".join([arg for arg in sys.argv[1:]])
    os.system("rmdir %s" % command)
else:
    print "No action taken!"
```

Simple example...

---

### Post by y-lee on 2008-02-19
> How would that work with the .bashrc? I can't I run a python script from within the bashrc?
Can I?

I thought you could but  I wasn't sure never even messed with my .bashrc file nor am I really a python programmer But I wrote a simple script and saved it.

Added **alias TMP=' python pyscript.py'** to .bashrc and it worked like a charm. TMP is of course what i call the command and pyscript.py is the script which by the way takes arguments. Of course your scripts have to be in your PATH or in the current directory.

EDIT: Well no  fast enough. lol

---

### Post by seventhc on 2008-02-19
> **pointone said:**
> ```
alias rmdir='/path/to/your/script'
``````
#! /usr/bin/env python

import sys, os

response = raw_input("Are you sure you want to remove the directory '%s'? " % sys.argv[1])
if response.lower() in ["y", "ye", "yes"]:
    command = " ".join([arg for arg in sys.argv[1:]])
    os.system("rmdir %s" % command)
else:
    print "No action taken!"
```Simple example...
cool, that code worked as I needed. I just had to use chmod first. Not sure if it needed to be made executable but I did that to.
Thanks :)
This actually helped me with my muttrc too b/c I have a python script I want to use in it, but I didn't know how. Now I do. :):)

---

### Post by pointone on 2008-02-19
Glad to have helped! And yes, I forgot to mention you need to chmod +x the script.

---

### Post by seventhc on 2008-02-20
I did 
chmod +x alias.py
chmod 755 alias.py
the first time I ran it it got permission denied, so I just did those and now it works perfectly. :)
I'm not sure if it's necessary but anytime I make a script executable I usually give it 755 permissions too.

---

