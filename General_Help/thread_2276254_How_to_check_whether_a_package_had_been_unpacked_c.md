---
title: "How to check whether a package had been unpacked correctly or not?"
date: 2015-05-01
forum: General Help
---

### Post by newbie14 on 2015-05-01
What to type in the terminal of an offline ubuntu computer to check whether a libgfortran3_4.8.2-19ubuntu1_i386.deb package file had been unpacked correctly or not?
I have tried typing
```

apt-cache policy libgfortran3_4.8.2-19ubuntu1_i386.deb

```
in the terminal, and using home folder as a current working directory, and the terminal replied:
```

N: Unable to locate package libgfortran3_4.8.2-19ubuntu1_i386.deb 
N: Couldn't find any package by regex 'libgfortran3_4.8.2-19ubuntu1_i386.deb'

```
And then I changed the current working directory to the directory where the original  libgfortran3_4.8.2-19ubuntu1_i386.deb package file is located, and then I typed
```

apt-cache policy libgfortran3_4.8.2-19ubuntu1_i386.deb

```
in the terminal, and then terminal also replied with:
```

N: Unable to locate package libgfortran3_4.8.2-19ubuntu1_i386.deb 
N: Couldn't find any package by regex 'libgfortran3_4.8.2-19ubuntu1_i386.deb'

```
From the reply of the terminal, I cannot conclude whether the  libgfortran3_4.8.2-19ubuntu1_i386.deb had been correctly unpacked or not. And I am not even sure the
```

apt-cache policy package_name

```
is the correct command to type in the terminal to check whether a libgfortran3_4.8.2-19ubuntu1_i386.deb package file had been unpacked correctly or not.
I am certain that the libgfortran3_4.8.2-19ubuntu1_i386.deb package file had been unpacked some days ago, but my brain's (possessive of brain, brains? brain's? brain'?) memory is unreliable. My questions is:

1: What to type in the terminal of an offline ubuntu computer to check whether a libgfortran3_4.8.2-19ubuntu1_i386.deb package file had been unpacked correctly or not?

[B]SOLUTION:

[/B]Type in:
```

[COLOR=#000000]dpkg -l libgfortran3[/COLOR]

```
If it starts 'ii' it means it installed and configured correctly.

---

### Post by CantankRus on 2015-05-01
You just want the package name without version or deb extension.
eg
```
apt-cache policy libgfortran3
```

---

### Post by newbie14 on 2015-05-01
> **CantankRus said:**
> You just want the package name without version or deb extension.
eg
```
apt-cache policy libgfortran3
```

Hey, it worked like a charm. Thank you user CantankRus

---

### Post by btindie on 2015-05-01
If you use the dpkg command it'll give you more information about the installed status. 'apt-cache policy' is meant for showing the priority of the package.
```
dpkg -l libgfortran3
```
If it starts 'ii' it means it installed and configured correctly.

---

### Post by newbie14 on 2015-05-01
> **btindie said:**
> If you use the dpkg command it'll give you more information about the installed status. 'apt-cache policy' is meant for showing the priority of the package.
```
dpkg -l libgfortran3
```
If it starts 'ii' it means it installed and configured correctly.

thank you very much, user btindie

---

### Post by newbie14 on 2015-05-01
So, I have tried this
```
dpkg -l libgfortran3
```
and the terminal replied with this:
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libgfortran3:i 4.8.2-19ubun i386         Runtime library for GNU Fortran a

```

My questions are:
1. What does "Desired=Unknown/Install/Remove/Purge/Hold" means?
2. What does "| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend" means?
3. What does "|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad) means?
4. does the "ii" mentioned earlier on the post: > **btindie said:**
> If it starts 'ii' it means it installed and configured correctly. is the same "ii" with the "ii" on the sixth line of the reply of the terminal?

---

### Post by btindie on 2015-05-01
The first 3 lines tell you what possible values you can have as the first 3 characters, generally it's just the 2 characters that are listed below the 5th line starting '+++'

'dpkg -l' is shorthand for 'dpkg-query -l' so if you type 'man dpkg-query' it'll tell you about it. ([http://man7.org/linux/man-pages/man1/dpkg-query.1.html](http://man7.org/linux/man-pages/man1/dpkg-query.1.html))

The 'ii' on the 6th line tells you that the Desired action is Install (1st i) and the Package status is Installed (2nd i) the 3rd character is missing as that's to indicate an error.

---

### Post by newbie14 on 2015-05-01
> **btindie said:**
> The 'ii' on the 6th line tells you that the Desired action is Install (1st i) and the Package status is Installed (2nd i) the 3rd character is missing as that's to indicate an error.

Thank you very much, user btindie.

Now I have 1 question.
how to fix the error at the third, blank character?

---

### Post by Bashing-om on 2015-05-01
newbie14; Hello;

> **newbie14 said:**
> Thank you very much, user btindie.

Now I have 1 question.
how to fix the error at the third, blank character?

That not having a character in that 3rd field is a good thing, That does mean there is not an error condition to report .

'ii' and
[INDENT][INDENT][INDENT]all is good
[/INDENT][/INDENT][/INDENT]

---

### Post by newbie14 on 2015-05-01
> **Bashing-om said:**
> newbie14; Hello; That not having a character in that 3rd field is a good thing, That does mean there is not an error condition to report .'ii' and all is good

Thank you user Bashing-om. Now I can understand the manual page more easily. Before I read your info, I don't understand a sentence in the manual page.

---

