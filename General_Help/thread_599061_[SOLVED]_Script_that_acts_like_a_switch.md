---
title: "[SOLVED] Script that acts like a switch"
date: 2007-10-31
forum: General Help
---

### Post by amadeus266 on 2007-10-31
If this script works to start/stop Compiz-Fusion

```
#!/bin/bash
if ps ax | grep -v grep | grep compiz.real > /dev/null
then
killall compiz.real && xfwm4 | metacity --replace
else
compiz --replace
fi
```

Why doesn't this one work with conky?

```
#!/bin/bash
if ps ax | grep -v grep | grep conky
then
killall conky &&
else
conky

```

I'm sure I'm missing something simple but I'm definitely NOT a programmer. I have a single icon on my panel that starts or stops Compiz. I would like to have one for conky as well. Thanks in advance.

---

### Post by kast on 2007-11-01
try 

[B]#!/bin/sh
if ps ax | grep -v grep | grep conky > /dev/null
then
killall conky 
else
conky
fi[/B]

also try just running the grep command from the command line and see if it even find just the word conky.

**ps ax | grep -v grep | grep conky**

 killall is not a gentle command perhaps looking into getting just the process i.d and running a kill on that instead of killall.

try to get that to work first, and i can help you if your interested on just getting the process i.d later.

---

### Post by mdebusk on 2007-11-01
> **kast said:**
> killall is not a gentle command perhaps looking into getting just the process i.d and running a kill on that instead of killall.

This will get you the process ID:
```
ps ax | grep conky | grep -v grep | awk '{ print $1 }'
```

so killing a process would be:
```
kill -9 `ps ax | grep conky | grep -v grep | awk '{ print $1 }'`
```

The "pgrep" and "pkill" commands work too, but I seem to recall reading that they are not available on every system.

---

### Post by mdebusk on 2007-11-01
> **amadeus266 said:**
> Why doesn't this one work with conky?

```
#!/bin/bash
if ps ax | grep -v grep | grep conky
then
killall conky &&
else
conky
```


You're missing the final "fi", for one thing.

Try this one instead:
```

#!/bin/bash
pkill conky
conky

```

If conky is running, this should kill it and start it new. If it isn't running, the failure of pkill to kill it should (as far as I know) not interfere with anything.

---

### Post by amadeus266 on 2007-11-03
The final "fi" is there it just didn't get copied over when I originally posted. The script in it's current form will kill conky but won't start it. The one for compiz works perfectly so I only need one icon and one click to start it or stop it as needed. I have tried the other suggestions posted up to here but I get the same results. Thanks to you all so far. Anyone else have some input?


Code:

#!/bin/bash
pkill conky
conky



This script will start conky but when running it again to stop conky it stops and then rstarts it.

---

### Post by mdebusk on 2007-11-04
> **amadeus266 said:**
> This script will start conky but when running it again to stop conky it stops and then rstarts it.

I'm sorry. I thought that was what you wanted. Does this do it?

```

#!/bin/bash
if pgrep conky; then
    pkill conky && exit
else
    conky
fi
exit

```

---

### Post by amadeus266 on 2007-11-04
> **mdebusk said:**
> I'm sorry. I thought that was what you wanted. Does this do it?

```

#!/bin/bash
if pgrep conky; then
    pkill conky && exit
else
    conky
fi
exit

```

This one will stop conky if it is running but will not start conky if not running.

---

### Post by mdebusk on 2007-11-04
> **amadeus266 said:**
> This one will stop conky if it is running but will not start conky if not running.

Weird. I'm no bash programmer (obviously), but I can think in a straight line and I don't see the problem.

This one is my last shot:
```

#!/bin/bash
if pgrep conky; then
    pkill conky
    exit
fi
conky

```

---

### Post by amadeus266 on 2007-11-05
> **mdebusk said:**
> Weird. I'm no bash programmer (obviously), but I can think in a straight line and I don't see the problem.

This one is my last shot:
```

#!/bin/bash
if pgrep conky; then
    pkill conky
    exit
fi
conky

```

That doesn't work either but thanks for your help. I'm sure I will figure this out sooner or later and when I do I will post it here to share with whoever would like such a script.

---

### Post by mdebusk on 2007-11-05
> **amadeus266 said:**
> That doesn't work either but thanks for your help.

I posted a question in Usenet newsgroup comp.unix.shell, which is an amazing resource.

Scott McMillan asked if conky was in your path. If it's not, that would explain the trouble you're having with starting it, and you should therefore use the full path to conky.

Bill Marcum suggests this:
```
killall conky 2>/dev/null || conky &
```

---

### Post by BennBuntu on 2007-11-06
> Bill Marcum suggests this:
```
killall conky 2>/dev/null || conky &
```

that one works for me

---

### Post by mdebusk on 2007-11-06
Sorry, gang... posted it twice by mistake.

---

### Post by amadeus266 on 2007-11-13
> **mdebusk said:**
> I posted a question in Usenet newsgroup comp.unix.shell, which is an amazing resource.

Scott McMillan asked if conky was in your path. If it's not, that would explain the trouble you're having with starting it, and you should therefore use the full path to conky.

Bill Marcum suggests this:
```
killall conky 2>/dev/null || conky &
```


That did it!!! I can now turn conky on or of with a single click of a single icon.  Thankyou so much.

---

### Post by amadeus266 on 2007-11-21
Here is the  instructions to do what I just did.

step 1: create an empty text file in your home directory, open it and put the following script in it.
setp 2: create a link on your panel that links to the test file created in step 1.

Now when you click your link, it will turn compiz or or off depending on whether it is running or not.

```
#!/bin/bash
if ps ax | grep -v grep | grep compiz.real > /dev/null
then
killall compiz.real && xfwm4 | metacity --replace
else
compiz --replace
fi
```

this one is for conky

```
#!/bin/bash
if ps ax | grep -v grep | grep conky
then
killall conky 2>/dev/null || conky &
else
conky
fi
```

---

### Post by amadeus266 on 2008-01-14
IF anyone wants a more elegant package Forlong published one on his blog.

[http://forlong.blogage.de/article/add_comment/1288#comments](http://forlong.blogage.de/article/add_comment/1288#comments)

---

