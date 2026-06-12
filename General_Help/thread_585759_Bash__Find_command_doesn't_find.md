---
title: "Bash : Find command doesn't find?"
date: 2007-10-21
forum: General Help
---

### Post by tacubuntuforums on 2007-10-21
Hi:
Can somebody explain me why bash gives me these _successive_ results when searching for a file:

```
user@host:~$ find /media/winA/Canned_Heat -iname *gene*
user@host:~$ find /media/winA/Canned_Heat -iname *parthe*
/media/winA/Canned_Heat/Canned Heat - 11 - Parthenogenesis.Mp3
user@host:~$ find /media/winA/Canned_Heat -iname *gene*
user@host:~$ find /media/winA/Canned_Heat -iname *genesis*
/media/winA/Canned_Heat/Canned Heat - 11 - Parthenogenesis.Mp3
user@host:~$ find /media/winA/Canned_Heat -iname *gene*
user@host:~$ find /media/winA/Canned_Heat -iname *gen*
user@host:~$ find /media/winA/Canned_Heat -iname *genes*
/media/winA/Canned_Heat/Canned Heat - 11 - Parthenogenesis.Mp3
user@host:~$ find /media/winA/Canned_Heat -iname *enes*
/media/winA/Canned_Heat/Canned Heat - 11 - Parthenogenesis.Mp3
user@host:~$ find /media/winA/Canned_Heat -iname *ene*
user@host:~$ find /media/winA/Canned_Heat/ -iname *ene*
user@host:~$ find /media/winA/Canned_Heat/ -name *ene*
user@host:~$ find /media/winA/Canned_Heat/ -name *gene*
user@host:~$ find /media/winA/Canned_Heat/ -name *ogene*
/media/winA/Canned_Heat/Canned Heat - 11 - Parthenogenesis.Mp3
user@host:~$ find /media/winA/Canned_Heat/ -name *sis*
/media/winA/Canned_Heat/Canned Heat - 11 - Parthenogenesis.Mp3
user@host:~$ find /media/winA/Canned_Heat/ -name *par*
user@host:~$ find /media/winA/Canned_Heat/ -iname *par*
user@host:~$ find /media/winA/Canned_Heat/ -iname *part*
user@host:~$ find /media/winA/Canned_Heat/ -iname *parth*
/media/winA/Canned_Heat/Canned Heat - 11 - Parthenogenesis.Mp3
user@host:~$ find /media/winA/Canned_Heat/ -iname *art*
user@host:~$ find /media/winA/Canned_Heat/ -iname *arth*
/media/winA/Canned_Heat/Canned Heat - 11 - Parthenogenesis.Mp3
user@host:~$ find /media/winA/Canned_Heat/ -iname *rth*
/media/winA/Canned_Heat/Canned Heat - 11 - Parthenogenesis.Mp3
user@host:~$ find /media/winA/Canned_Heat/ -iname *hen*
/media/winA/Canned_Heat/Canned Heat - 11 - Parthenogenesis.Mp3
user@host:~$ find /media/winA/Canned_Heat/ -iname *heno*
/media/winA/Canned_Heat/Canned Heat - 11 - Parthenogenesis.Mp3
user@host:~$ find /media/winA/Canned_Heat/ -iname *eno*
/media/winA/Canned_Heat/Canned Heat - 11 - Parthenogenesis.Mp3
user@host:~$ find /media/winA/Canned_Heat/ -iname *gen*
user@host:~$ find /media/winA/Canned_Heat/ -iname **gen*
user@host:~$ find /media/winA/Canned_Heat/ -iname **gene*
user@host:~$ find /media/winA/Canned_Heat/ -iname **genes*
/media/winA/Canned_Heat/Canned Heat - 11 - Parthenogenesis.Mp3
user@host:~$ find /media/winA/Canned_Heat/ -iname *gen*p3
/media/winA/Canned_Heat/Canned Heat - 11 - Parthenogenesis.Mp3
user@host:~$ find /media/winA/Canned_Heat/ -iname *gen*M*
/media/winA/Canned_Heat/Canned Heat - 11 - Parthenogenesis.Mp3
user@host:~$ find /media/winA/Canned_Heat/ -iname *gen**
user@host:~$
```


Thank you.

BTH, I also have an old unresolved problem regarding Bash, pipes and output formats in:
[http://ubuntuforums.org/showthread.php?t=499626](http://ubuntuforums.org/showthread.php?t=499626)

---

### Post by kidders on 2007-10-22
Hi there,

I don't think any of these commands is doing what you think it's doing. Not all shells behave the same way, but in Bash, there is a *world* of a difference between **find -name foo*** and **find -name "foo*"**.

For instance, imagine you did the following:```
cd ~
touch XXXpartheYYY
find /media/winA/ -iname *parthe*
```
Bash would expand the '*parthe*' argument in the "find" command, so only files in /media/winA or below called "XXXpartheYYY" would be returned.

Luckily, the commands you executed don't modify any files ... in other circumstances, Linux could've crucified you for leaving special characters unquoted, when you mean them literally.

> I also have an old unresolved problem regarding Bash, pipes and output formatsThat thread seems to have been thoughrally answered. :confused:

---

### Post by tacubuntuforums on 2007-10-27
Thanks.

Yes, you don't say it clearly, but the apostrophes surrounding the expression were missing

Don't worry I never execute commands that modify things that another command outputs and things like that without testing first  :-)

As regards my other thread, yes, there are many comments there, but none is a walk around to the problem. I'm still waiting for one.

---

### Post by kidders on 2007-10-27
> **tacubuntuforums said:**
> Yes, you don't say it clearly, but the apostrophes surrounding the expression were missingSorry for the lack of clarity. The point I was trying to make, I suppose, is that the quotes weren't *missing* per se ... your commands are perfectly valid without them ... they just do something a bit different.

This distinction (ie between literal characters & symbolic characters) is very useful, and crops up a lot in Linux.

All the best. :-)

---

