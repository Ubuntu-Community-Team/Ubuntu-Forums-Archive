---
title: "Why does ./pythonScript.pyc not work in ubuntu server?"
date: 2007-08-16
forum: General Help
---

### Post by RawMustard on 2007-08-16
This has got me completely stumped :(

I can type ./bashScript.sh and it works.  I can type ./PythonScript.py and it works. But if I type ./PythonScript.pyc it doesn't work.  If I type python PythonScript.pyc it works.  How can I make it work so I can type ./PythonScript.pyc?

Some help on this would be mucho's appreciated.

Oh I should have added that it works fine in a desktop install of feisty, just not the sever install.

---

### Post by kidders on 2007-08-17
Hi there,

Filenames are irrelevant ... you should check that your Python script is valid and executable.

---

### Post by pointone on 2007-08-17
Just to point out: There's no need to ever run the *.pyc files directly. If you run a *.py file in the same directory as a *.pyc file (same name, mind you) then Python will use the compiled file provided there have been no changes in your *.py file since the *.pyc's creation. In summary:

./PythonScript.py == ./PythonScript.pyc

---

### Post by RawMustard on 2007-08-18
Yeah I know that, but something is wrong with ubuntu's server version of python.  I should be able to pre-compile large scripts to byte code and execute them without need of the original py file but it doesn't work.

---

### Post by RawMustard on 2007-08-18
> **kidders said:**
> Hi there,

Filenames are irrelevant ... you should check that your Python script is valid and executable.

Hi again Kidders.

Yep that's not the problem, something's up with python on ubuntu server.
check my post in programming talk for more info.
[http://ubuntuforums.org/showthread.php?t=526865]("http://ubuntuforums.org/showthread.php?t=526865")

---

### Post by kidders on 2007-08-18
> **RawMustard said:**
> Yep that's not the problem, something's up with python on ubuntu server.Yeah... I completely misunderstood your problem ... hence my clearly idiotic response hehe. Sorry about that.

---

