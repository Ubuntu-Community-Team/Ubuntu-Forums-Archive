---
title: "bash script - search for installed file (i'm stuck)"
date: 2008-01-31
forum: General Help
---

### Post by frediE on 2008-01-31
any help with a bash script that does this?

search for installed version of package
if doesn't exist (or not the current version i want) then download from web and install

guessing it's going to me more then my 2 lines above.  but any direction would be awesome.

i have tried searching with the following..  and if it doesn't exist then it **doesn't** print anything and i get "echo1"...... (which seems to be working) but if it **does** exist then i get "line 2: [: too many arguments"

> #!/bin/bash
if [ -n $(aptitude search ~nPACKAGENAME~V0.12) ]; then
	echo "echo1"
else 
	echo "echo2"
fi

---

### Post by chewearn on 2008-01-31
Change the if statement line to:
```
if [ -n "`aptitude search ~nPACKAGENAME~V0.12`" ]; then
```

Note the doublequote and backqoute used.

---

### Post by frediE on 2008-02-01
thanks for the suggestion.  :-)

when i try the double & single quotes, I "echo1" back every time.  Weather the statement is true or false.
any other suggestions?  -thanks

---

### Post by chewearn on 2008-02-01
Not singlequote, but backquote.  If you have a US keyboard, its the "lowercase" of the tilda key, below ESC.

---

### Post by frediE on 2008-02-01
oh the young padawan has much to learn.  thanks much, it works like a champ.
ehco1 = good
echo2 = bad


can i assume the code in the backquote is executed and the double quote is to deal with spaces?

---

### Post by chewearn on 2008-02-01
Yes, strings inside backquotes are executed first.  Then, the output is converted to string by the doublequotes, so that the if statement can interpret correctly.

---

### Post by frediE on 2008-02-01
awesome, thanks again for the help!

---

