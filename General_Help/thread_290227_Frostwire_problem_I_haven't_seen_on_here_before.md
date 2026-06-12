---
title: "Frostwire problem I haven't seen on here before"
date: 2006-10-31
forum: General Help
---

### Post by voodoonirvana on 2006-10-31
OK first off, I DO have the latest JRE installed, and I HAVE tried running it from the terminal. I installed it with automatix 2 and first tried clicking on the icon in Ap[plications>Internet, but got nothing. I then tried running it from the terminal and got something I had never seen before. I looked up frostwire on here and it was mostly people who didn't have JRE or something but here is the error I got:

[b]
sam@sam-laptop:~$ frostwire
runFrost.sh: 44: Syntax error: "(" unexpected (expecting "}")
[/b]

Oh and I'm using dapper.

---

### Post by DougieFresh4U on 2006-10-31
Re: dash to bash
the first way (easy, one step):
Code:

sudo ln -sf /bin/bash /bin/sh

or (better) find the script which launch frostwire:
Code:

which frostwire

should give you a result like this: /usr/bin/frostwire
then:
Code:

gksudo gedit /usr/bin/frostwire

at the beginning of file, you ll find a line:
Code:

#!/bin/sh

replace sh with bash in this line                                                 **this is for edgy**

---

### Post by voodoonirvana on 2006-10-31
> **DougieFresh4U said:**
> Re: dash to bash
the first way (easy, one step):
Code:

sudo ln -sf /bin/bash /bin/sh

or (better) find the script which launch frostwire:
Code:

which frostwire

should give you a result like this: /usr/bin/frostwire
then:
Code:

gksudo gedit /usr/bin/frostwire

at the beginning of file, you ll find a line:
Code:

#!/bin/sh

replace sh with bash in this line                                                 **this is for edgy**

Okay when I try the first code, it does absolutely nothing. Just acts as it would if you hit enter and moves on to wait for another command.

When I try the "which frostwire" command it says usr/bin/frostwire, but I cant even change to that directory or anything. And when I try and do the "gksudo gedit usr/bin/frostwire" command it gives me this:
[b]
(gedit:9174): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
[/b]
and opens up gedit but there is no text.

Gksudo doesn't even work for dapper does it? Kinda new at this, so sorry for the ignorance. Nobody would answer in the beginners forum.

---

### Post by DougieFresh4U on 2006-10-31
with dapper you should not worry about the dash to bash. only edgy. do you have both java?** Sun Java 5 and Java 1.4 or 1.5**

---

### Post by voodoonirvana on 2006-10-31
> **DougieFresh4U said:**
> with dapper you should not worry about the dash to bash. only edgy. do you have both java?** Sun Java 5 and Java 1.4 or 1.5**

Yes, I have all the Java packages needed Im pretty sure. Well at least I don't see any important ones unchecked in the synaptic package manager. Is there another way I can check this? I'm positive I have Sun Java 5 but I mean with the other(s).

---

### Post by DougieFresh4U on 2006-10-31
on forum home page, in the blue space (find answers quickly) type **frostwire **  and it will bring you to some more info. hope it helps!!          Applications>Add/Remove when that opens -make sure that box is checked for unsupported and also the othe box. i am not sure the what its called but I remember going through the same problem.

---

### Post by canadianwriterman on 2006-10-31
This was corrected with the latest version of Automatix2. If you uninstall Frostwire, then use Automatix2 to install it, it should be fine. Worked for me when I had the same problem.

---

### Post by voodoonirvana on 2006-10-31
> **canadianwriterman said:**
> This was corrected with the latest version of Automatix2. If you uninstall Frostwire, then use Automatix2 to install it, it should be fine. Worked for me when I had the same problem.

No that wasn't working either but I got it figured out! :)

What I had to do was run a java config and use Sun's java option, and that lead it to the right java path or and it started up! :)

Thanks for the help though.

---

