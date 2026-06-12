---
title: "python issue (involving adesklets)"
date: 2008-04-24
forum: General Help
---

### Post by conartist6 on 2008-04-24
I'm trying to run an adesklets desklet, which is a simply .py file. 

The opening of the py file reads like this:

```
from math import *
from adesklets.commands import *
import adesklets
from time import time
from random import randint
from statgrab import *
from os.path import join
import ConfigParser
import string
import re

class Monitor:
    def __init__(self, config, skin):
        self.config = {}
        self.convert_config( config )        
        self.etcetcetc
```

and the terminal output reads thusly:

```

conartist6@T61:~/.desklets$ ./circlemeter.py --nautilus
from: can't read /var/mail/math
from: can't read /var/mail/adesklets.commands
from: can't read /var/mail/time
from: can't read /var/mail/random
from: can't read /var/mail/statgrab
from: can't read /var/mail/os.path
./circlemeter.py: line 12: class: command not found
./circlemeter.py: line 13: syntax error near unexpected token `('
./circlemeter.py: line 13: `    def __init__(self, config, skin):'
```

/var/mail is an empty folder, and seems pretty obviously not to contain the files the program is looking for. So first, since my indexing is being broken (thats my next project, along with resizing my linux partition), where are these files that the script is looking for? And second, of course, how do I tell the script where they are? Thanks in advance for teh help.

---

### Post by conartist6 on 2008-04-28
Eh, thanks for the help, it turned out the maker of the script forgot to specify the directory to python at the beginning...

---

### Post by Doctor Drive on 2009-11-20
Hey, I didn't quite understand what was the problem. Can u explain what to do to prevent that please?

---

### Post by conartist6 on 2009-11-20
#! /bin/python, or somesuch depending on where your python interpreter lives. I think thats what I meant. I don't even use ubuntu anymore and the copy of it I was messing with adesklets on is long gone, but from what I posted earlier that would be the missing link.

---

### Post by Doctor Drive on 2009-11-20
sorry, still didn't get it.
what file should I modify?

---

### Post by conartist6 on 2009-11-20
Looks like I was working with the custom widget circlemeter.py. What are you working with? Explain...

---

### Post by Doctor Drive on 2009-11-20
ok... the problem is like this:

when I launch

> 
[email]doctor@Doctor:~/.deskle[/email]ts/CircleMeter$ python mem_meter.py --nautilus


It works when testing but doesn't register
If I launch like that
> 
[email]doctor@Doctor:~/.deskle[/email]ts/CircleMeter$ ./mem_meter.py --nautilus


it crashes
> 
from: can't read /var/mail/circlemeter
./mem_meter.py: line 3: syntax error near unexpected token `('
./mem_meter.py: line 3: `class MemMeter( Monitor ):'



It happens with every *meter.py

---

### Post by conartist6 on 2009-11-20
And mem_meter.py does or does not begin with a #!/bin/python style line... ? I'm not even sure I ever got my desklets to register... But that was a while ago. Maybe things are better now or you'll figure it out. If you keep posting error codes up here I'd be willing to help you work through them for the benefit of anybody else who comes along later looking to do this.

---

### Post by Doctor Drive on 2009-11-20
none of *.py scripts begin with  #!/bin/python line...
I don't really think they should... or should they?

----------------

if I add that it says
> 
[email]doctor@Doctor:~/.deskle[/email]ts/CircleMeter$ ./mem_meter.py --nautilus
bash: ./mem_meter.py: /bin/python: bad interpreter: No such file or directory


---

### Post by conartist6 on 2009-11-20
Yeah, they all should. The bash interpreter is trying to read them at the moment. That is why calling them via the python command works but not calling them as scripts. In linux (and windwos) the extension of a file usually has almost no meaning aside from helping the user figure out what it should do. In this case running an executable script with the .py extension doesn't guarantee that it will be sent to the python interpreter. Apologies if you knew that already.

---

### Post by Doctor Drive on 2009-11-20
well, ok but running like script, for example "./weather.py", worked fine.
but CircleMeter doesn't.

So what should be the problem?
and if I add #!/bin/python to a script:
> 
bash: ./mem_meter.py: /bin/python: bad interpreter: No such file or directory


so that doesn't look like solution... :(

---

### Post by conartist6 on 2009-11-20
Apologies, I was quoting you bin/python as a placeholder for wherever the python interpreter really lives, a location which I have forgotten. Run
 ```
whereis python
```
from the command line to find out where your python interpreter lives. On my slackware64 system that is /usr/bin/python2.6, which sounds like it might be the same for Ubuntu as well...

---

### Post by Doctor Drive on 2009-11-20
my python was in #!/usr/bin/python

ok, thanks. now I can register it.

I've registered cpu_meter,
but the cpu_meter adesklet woun't appear while executing
alt+f2
adesklets --nautilus

it shows only weather adesklet which I've registered earlier.

but while executing adesklets --nautilus in console everything shows up...

---

### Post by Doctor Drive on 2009-11-20
kinda strange issue but the main problem is solved.
Thanks a lot conartist6 !!

---

### Post by conartist6 on 2009-11-22
I'm not sure why the console would make a difference... You could try running (from alt f2) something like "sh adesklets --nautilus&". I guess if you're planning to put the command in rc.local it doesn't matter since you will be running it from the command line. Anyway, glad it worked out. Have fun with adesklets, and hope you're liking Ubuntu.

---

### Post by Doctor Drive on 2009-11-23
That wasn't a console.
-----
It appeared that I have to launch adesklets from CircleMeter dir to make CircleMeter appear.

```

doctor@Doctor:~$ adesklets --nautilus

```

adesklets will launch without CircleMeter
-------------------------------------
```

doctor@Doctor:~/.desklets/CircleMeter$ adesklets --nautilus

```

that way CircleMeter will appear...

o_O

It seems CircleMeter is kind'a buggy - it caused many problems during configuring.

---

