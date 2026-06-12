---
title: "Setting environment variable by reference"
date: 2013-11-08
forum: General Help
---

### Post by helloworld1215 on 2013-11-08
Is there a way to specify that an environment variable is composed of a different environment variable so a change is propagated to the environment variable referencing said variable?

export TEST=1
export TEST2=$TEST 

Doesn't work...

---

### Post by TheFu on 2013-11-08
Which shell?  Different shells work differently.

sh/bash/ksh use export ... like you are showing.
csh/tsch use set/setenv .... 
I suspect zsh and the 20 others use something different, but I do not know.

BTW, that DOES work here. Some sample code:
```
#!/bin/bash

export TEST=1
export TEST2=$TEST 

echo "Test is: $TEST"
echo "Test2 is: $TEST2"
```

If you don't need the variable(s) to be passed anywhere outside the script, then you can leave off the "export" too.
```
#!/bin/bash

 TEST=1
 TEST2=$TEST 

echo "Test is: $TEST"
echo "Test2 is: $TEST2"
```

That works as well.

In case it is not clear, I tested BOTH of those scripts. Both work and I don't see any reason they would not work on any UNIX/Linux OS with bash installed.  Heck, sh (Borne Shell) can run them too, unchanged.

However, if the TEST=1 line is not a single word, then it is very important to quote the variables in the assignment AND later in the script in the use points.
```
#!/bin/bash
 TEST="something with more words"
 TEST2="$TEST"
echo Test is: "$TEST"
echo Test2 is: "$TEST2"
```
This works too.
```
$ ./tttt 
Test is: something with more words
Test2 is: something with more words

```

---

### Post by drmrgd on 2013-11-08
As TheFu says, this should work fine, and knowing what shell you're using would be key.  This method is most often used in adding binary containing paths to your $PATH variable:

```

# In something like .bashrc
export PATH=$PATH:$HOME/some_program_directory/bin

```

Now if you echo $PATH in the terminal you'll see that the new path was added to the list of paths already contained in $PATH.

Another thing to consider is reloading the shell when you make changes like that.

---

### Post by steeldriver on 2013-11-08
... by "change is propagated" I'm guessing the OP means that the **value** of TEST2 should change if the **value** of TEST is subsequently modified? afaik the variable on the RHS of an assignment is expanded once, at assignment time - so no

---

### Post by TheFu on 2013-11-08
> **steeldriver said:**
> ... by "change is propagated" I'm guessing the OP means that the **value** of TEST2 should change if the **value** of TEST is subsequently modified? afaik the variable on the RHS of an assignment is expanded once, at assignment time - so no

Ah - he wants a pointer reference in a shell script?  No gonna happen.  Assignments are "copy on assignment" - they do not point to the same memory location.  He would need a different language for that ... Perl, C, C++, pascal, .... perhaps Java (don't know). Look for something with lots of "pointers" or "references" clearly used in the specification and training.  My knowledge of popular languages used today is weak, but [RosetteCode]("http://rosettacode.org/") might provide some options from 500+ languages and 500+ real-world example solutions in each language.  Found a "[pointers and references]("http://rosettacode.org/wiki/Pointers_and_references")" link there. Some interesting solutions - sh and bash are NOT in the list of solution languages.

---

