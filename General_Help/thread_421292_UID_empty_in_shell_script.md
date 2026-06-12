---
title: "UID empty in shell script"
date: 2007-04-24
forum: General Help
---

### Post by caphrim007 on 2007-04-24
This is really bugging me, and I guess I can't call it a bug even though imho it is

/bin/sh on ubuntu is linked to /bin/dash which I guess is a crippled shell that debian uses for whatever reason. Well, one of the pieces of the shell that apparently is non POSIX compliant is the UID environment variable (among others).

A simple shell script on Feisty

#!/bin/sh
echo $UID

echos nothing, while

#!/bin/bash
echo $UID

echos the ID. fyi in case anyone runs into it too.

Isn't this one of those things that has the potential of breaking shell scripts? Most of the examples I see these days use /bin/sh with the assumption that bash is running under the hood.

Thanks,
Tim

---

### Post by dannyboy79 on 2007-04-24
great discovery but apparently you should never assume what /bin/sh is linked to. I can't say whether it should be mapped to bash or not since I didn't develop the os. The developers probably have a good reason for it. Also, if you want to run a bash script, than maybe to make sure they would you should use 

#!/bin/bash

as the first line instead of counting on a symlink to achieve the same result. Wouldn't you agree?

---

### Post by caphrim007 on 2007-04-24
Agreed, making an assumption like that is foolish. It bit me though, and I'm not lucky enough to be the only person to run into this :-)

I guess I was just looking at it from the "examples online" point of view since most of them I see tend to make that assumption. 

Thanks,
-Tim

---

### Post by dannyboy79 on 2007-04-24
i suppose that is true. It still is good you pointed this out. It's to bad you can't change the title to say, /bin/sh linked to dash NOT bash. or you could just create a new thread. i am sure there are others like you which this dash will affect.

---

### Post by engla on 2007-04-24
Ubuntu "made the switch" to dash with release 6.10. So lots and lots of upstream authors have had bugfixes on that particular thing. Given how big ubuntu is, it really does something in terms of awareness for this type of thing. And linuxy people are generally careful with not assuming things.. we read docs when programming!

---

### Post by caphrim007 on 2007-04-24
> **engla said:**
> Ubuntu "made the switch" to dash with release 6.10. So lots and lots of upstream authors have had bugfixes on that particular thing.

Ok, np, I've only recently started using Ubuntu, so I wasn't even aware of the switch. No harm no foul, Google didn't come back with anything immediate so that's why I came here to ask. Turns out I answered my own question before I posted, so I decided to post anyway in case someone else came around looking.

-Tim

---

