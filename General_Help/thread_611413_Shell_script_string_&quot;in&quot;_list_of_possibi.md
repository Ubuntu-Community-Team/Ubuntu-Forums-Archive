---
title: "Shell script string &quot;in&quot; list of possibilities"
date: 2007-11-12
forum: General Help
---

### Post by dizwell on 2007-11-12
I'm writing a shell script which accepts a couple of parameters when invoked.

How can I check that one of the parameters supplied has one of four possible values?

That is, I invoke the script like so:

```
myscript.sh apple
```

I want the script to check that the user has supplied one of 'apple', 'pear' or 'banana'. I can do it the hard way:

```
if [ $1 = "apple" ]; then
  echo "You typed apple"
fi

if [ $1 = "pear" ]; then
  echo "You typed pear"
fi
```
 
...and so on. But I would like something more like:

```
if [ $1 IN "apple", "pear" or "banan" ]; then
  echo "You typed a correct value"
fi
```

I've looked at the string evaluation stuff in assorted places (such as [http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)) but I'm either missing it or it's not there in the first place... but either way, I'm stuck!

Grateful for any help.
Regards
HJR

---

### Post by MrFSL on 2007-11-12
It's not pretty but this gives the desired effect:
```
#!/bin/bash

if [ "$1" = "apple" ]; then
	echo "You typed a correct value"
else
	if [ "$1" = "pear" ]; then
		echo "You typed a correct value"
	else
		if [ "$1" = "banana" ]; then
			echo "You typed a correct value"
		fi
	fi
fi
```

---

### Post by MrFSL on 2007-11-12
This works to:
```
!/bin/bash

if [[ "$1" = "apple" || "$1" = "pear" || "$1" = "banana" ]]; then
	echo "You typed a correct value"

fi

```

---

### Post by MrFSL on 2007-11-12
As does this:
```
#!/bin/bash

if [ "$1" = "apple" -o "$1" = "pear" -o "$1" = "banana" ]; then
	echo "You typed a correct value"

fi

```

---

### Post by dizwell on 2007-11-13
Thanks. I definitely wanted to avoid nested ifs: the list could get quite long and it would be a nightmare to maintain.

I had actually tried your middle option  -the [[ "$1" = "apple" || "$1" = "pear" || "$1" = "banana" ]] one, but with only single square brackets. I wish I knew the difference, but an additional bracket either side fixes the problem, so thanks for a nice fix.

---

### Post by MrFSL on 2007-11-13
Yeah... this is why I gave up on bash and now use perl for everything I do.

---

### Post by nikhilk on 2007-11-13
> **dizwell said:**
> Thanks. I definitely wanted to avoid nested ifs: the list could get quite long and it would be a nightmare to maintain.
To avoid this problem bash supports "case" construct.
You can do something like this:
```
case $1 in
    apple)<do something>
              ;;
    pear)<do something>
             ;;
    <more checks>

```
Google if you need more information.

---

### Post by dizwell on 2007-11-13
Thanks. I'm using case within the rest of the shell script already. I didn't want nested case statements, either!

To explain: I have 

generic stuff I don't want to run unless the specific stuff is fine
case $1 in
apple)
pear)
banana)
*)

I therefore don't want part 1 of the script to execute unless I know in advance that a banana, pear or apple-specific bit is going to work fine. So, I want to check that the call to the script is formatted corrected. Now what I have (inpseudocode) is

if $1 ="apple"||"pear"||"banana"
generic stuff I don't want to run unless the specific stuff is fine
fi
case $1 in
apple)
pear)
banana)
*)

The if protects my generic stuff from being run unless the right parameters are supplied, then the case statement sorts out which parameter-specific bit runs. It might not be pretty, and I dare say there are more elegant ways of doing it, but it works, which is nice.

---

