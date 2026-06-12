---
title: "Do nothing in a script"
date: 2007-10-10
forum: General Help
---

### Post by jmvidalvia on 2007-10-10
It might seem to be an stupid question but, how can I write to "do nothing" in a script.
Till now I am using: echo "" > /dev/null
But there is for sure a better option.
Thanks!

---

### Post by Lord Illidan on 2007-10-10
I don't get what you mean here..
You want no output?

---

### Post by jmvidalvia on 2007-10-10
> **Lord Illidan said:**
> I don't get what you mean here..
You want no output?

Yes: I am using if & then, and I need no output for one condition...
thanks!

---

### Post by FRuMMaGe on 2007-10-10
If you tell us why you need it and for what purpose, I'm sure we could help you.

---

### Post by Lord Illidan on 2007-10-10
> **jmvidalvia said:**
> Yes: I am using if & then, and I need no output for one condition...
thanks!

Give us some code. But AFAIK sending it to /dev/null is the way it is done.

---

### Post by jmvidalvia on 2007-10-10
I have this script running as a crontab. it checks if a folder is empty. if it is, it must do nothing. If it is not empty, it must do things such as move, etc.
```
#!/bin/bash
if [ -z $(ls folder) ]
then
        echo "" > /dev/null
else
        /scripts/script.sh
fi

```
Thanks!

---

### Post by bodhi.zazen on 2007-10-10
you could also sleep

sleep 1

It would introduce a 1 second delay however, which could add up if you are looping ...

otherwise you can echo > /dev/null

---

### Post by dreadlord_chris on 2007-10-10
> **jmvidalvia said:**
> I have this script running as a crontab. it checks if a folder is empty. if it is, it must do nothing. If it is not empty, it must do things such as move, etc.
```
#!/bin/bash
if [ -z $(ls folder) ]
then
        echo "" > /dev/null
else
        /scripts/script.sh
fi

```
Thanks!

couldn't his be rearanged like this:
```

#! /bin/bash
if [ -n $(ls folder) ]
then
       /scripts/script.sh
fi

```
from BASH man pages:
> 
-z string == True if the length of string is zero.
-n string == True if the length of string is non-zero.


---

### Post by nick_h on 2007-10-10
Why don't you just write the script as:
```
#!/bin/bash
if ! [ -z $(ls folder) ]
then
        /scripts/script.sh
fi
```
or am I missing something?

EDIT: or even the solution in the previous post :)

---

### Post by jmvidalvia on 2007-10-11
-n string is the solution for me.
Thank you very much to all of you!
:)

---

### Post by nick_h on 2007-10-11
Yes the -n solution is neater in this case.  I left my post to illustrate the *not* operator.

---

