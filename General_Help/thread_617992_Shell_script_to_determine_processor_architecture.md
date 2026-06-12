---
title: "Shell script to determine processor architecture"
date: 2007-11-19
forum: General Help
---

### Post by dizwell on 2007-11-19
I want a shell script to check if it is running on the right sort of processor architecure (basically, i686 or x86_64).

I know _I_ can check with 'arch' and get the right result, but how do I get a shell script to run that command AND assign its value to a variable (let us call it $ARCH) so that I can do branching stuff depending on the value of $ARCH?

In other words, I want to be able to do something like

#!/bin/bash
arch > $ARCH
if [ $ARCH == 'i686' ]; then
  -do 32-bit things
fi

if [ $ARCH == x86_64' ]; then
  -do 64-bit things
fi

Any pointers, please?

---

### Post by Whiffle on 2007-11-19
try:

```

ARCH=`arch`

```

---

### Post by dizwell on 2007-11-19
I apologise for an earlier reply that said the above didn't work. It didn't, because when you wrote ARCH=`arch` I thought you meant ARCH='arch'

...I have not come across the difference between a straight quote and a backward-slanting apostrophe before! Could you explain what the difference between ` and ' is, please? (Apart from being fiendlishly similar on the screen?!)

---

### Post by avik on 2007-11-20
> **dizwell said:**
> 
...I have not come across the difference between a straight quote and a backward-slanting apostrophe before! Could you explain what the difference between ` and ' is, please? (Apart from being fiendlishly similar on the screen?!)

' is for quoting.  That's why it's a quote.

` is the backtick, and anything you put within it is replaced by its output in a shell.  Maybe you've seen something like:

```

sudo apt-get install linux-headers-`uname -r`

```

On my computer, the output of uname -r by itself is 2.6.22-14-generic, so the entire command is now:

```

sudo apt-get install linux-headers-2.6.22-14-generic

```

That allows people to substitute in unknown values that can be determined by running another program.

---

### Post by dizwell on 2007-11-20
Thanks for the explanation. Weird I've not heard of the backtick before -never had occasion to do what your last sentence says it does... and which was precisely my need here, of course. Google (now I know what to search for) here I come!

---

### Post by TomG24 on 2008-03-22
Hi all,

I want to do something similar, but depending on the architecture, I want to install a batch of .deb packages.

I wrote a script, but there seems to be still something wrong with it. For testing purposes, I used an "if-statement" and a "case-statement".

**Method 1: if**
```

#!/bin/bash

platform=`uname -m`
if [ "$platform"="i686" ]; then
	echo "32-bit OS"
	# Install necessary deb packages
elif [ "$platform"="X86_64" ]; then
	echo "64-bit OS"
	# Install necessary deb packages
else
	echo "Unknown platform"
	# Don't install any packages
fi

```

**Method 2: Case-statement**
```

#!/bin/bash

platform=`uname -m`
case $platform in
"i686")
  	echo "32-bit OS"
	# Install necessary deb packages
	;;
"X86_64")
	echo "64-bit OS"
	# Install necessary deb packages
	;;
*)
	echo "Unknown platform"
	# Don't install any packages
	;;
esac

```

The systems used are: a 32-bit Ubuntu 7.10 and a 64-bit Ubuntu 7.10.
On the 32-bit platform:
1st script says 32-bit
2nd script says 32-bit
So far, so good but:

On the 64-bit platform:
1st script: 32-bit
2nd script: Unknown platform

Probaly I forgot some details about Bash syntax. Someone who could help me out with this? Thank you.

---

