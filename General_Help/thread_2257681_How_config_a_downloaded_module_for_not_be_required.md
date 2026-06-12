---
title: "How config a downloaded module for not be required copy it for the .py script folder?"
date: 2014-12-21
forum: General Help
---

### Post by DiogoSaraiva on 2014-12-21
Hi everyone,
Is it possible configure a module for each time that I make a script in a different folder not be required copy the modules ("virtGPIO.py" and "serialConfig.py") for that folder.


Example I make a script:


```

#!/usr/bin/python
# -*- coding: utf-8 -*-


import virtGPIO as GPIO

```


and it gives me a error if I don't put the modules ("virtGPIO.py" and "serialConfig.py") in the same folder that the script is.

:KS[SIZE=3]Thanks you very much....[/SIZE]:KS

PS: It isn't a Raspberry Pi, that is why i'm using virtual GPIO using an arduino and a mini PC [SIZE=1](Giada A51B)[/SIZE]...
You can view this project at [https://github.com/BLavery/virtual-GPIO ]("https://github.com/BLavery/virtual-GPIO")
And sorry for my bad english, because I'm portuguese ](*,)

---

### Post by tgalati4 on 2014-12-21
```
echo $PATH
```

Append your path to include a directory that holds your common, shared libraries.  For some people, ~/bin is used, but it could be any directory in your home directory and then added to your path statement.

You could also put the shared libraries in a directory that already exists in your path, such as /usr/local/bin.

```
cd
cat .profile
```

You will notice that if ~/bin exists in your home directory, then it is automatically added to your path.  So adding ~/bin and putting your common modules there is a typical way to handle this issue.

I was going to suggest using an Arduino to get your GPIO's, but then you figured that out.

---

### Post by steeldriver on 2014-12-21
Hmm... does python really use PATH as its module search path? wouldn't that be PYTHONPATH?

---

### Post by DiogoSaraiva on 2014-12-21
I didn't understanded what should do I do?

Sorry... ](*,)

---

### Post by DiogoSaraiva on 2014-12-22
anyone?
Thanks

---

### Post by steeldriver on 2014-12-22
Not a python expert but I would try this: put the module files somewhere (e.g. create a directory $HOME/python) and then add that directory to your PYTHONPATH variable

```

export PYTHONPATH=$PYTHONPATH:$HOME/python

```

If that works, and you want to make it persistent, add the export command to your ~/.bashrc

Alternatively, if you have administrative rights you can put the modules somewhere that's already on python's path, which you can find by printing sys.path from the python shell

```

python -c 'import sys; print sys.path'

```

however I would not recommend that unless they really are standard modules that you want to make available system-wide.

---

### Post by DiogoSaraiva on 2014-12-22
[SIZE=2]look at this:
[/SIZE]
[SIZE=2]diogosaraiva@Ubuntu:~$ python -c 'import sys; print sys.path'[/SIZE]
[SIZE=2]['', '/usr/local/lib/python2.7/dist-packages/pip-1.5.6-py2.7.egg', '/home/diogosaraiva', '/usr/local/bin/virtGPIO-libraries', '/usr/lib/python2.7', '/usr/lib/python2.7/plat-x86_64-linux-gnu', '/usr/lib/python2.7/lib-tk', '/usr/lib/python2.7/lib-old', '/usr/lib/python2.7/lib-dynload', '/usr/local/lib/python2.7/dist-packages', '/usr/lib/python2.7/dist-packages', '/usr/lib/python2.7/dist-packages/PILcompat', '/usr/lib/python2.7/dist-packages/gtk-2.0', '/usr/lib/python2.7/dist-packages/ubuntu-sso-client'][/SIZE]
[FONT=Menlo][SIZE=2]

it have [/SIZE][FONT=Verdana]/usr/local/bin/virtGPIO-libraries[/FONT][SIZE=2]

but not work yet

[/SIZE]
[/FONT]

---

### Post by DiogoSaraiva on 2014-12-23
anyone,
is not solved yet?
Thanks

---

### Post by DiogoSaraiva on 2014-12-26
[SIZE=3]Solved...
With only 2 commands and with an previous copy-paste:[/SIZE]

**[SIZE=2][FONT=arial black]echo export PYTHONPATH='$PYTHONPATH':/usr/lib/python2.7/virtGPIO >> ~/.bash_profile[/FONT][/SIZE]**
and
[B][SIZE=2][FONT=arial black]source ~/.bash_profile
[SIZE=4][FONT=comic sans ms]
Thanks to all... and a happy new year [/FONT][/SIZE]
[/FONT][/SIZE][/B]

---

### Post by DiogoSaraiva on 2014-12-30
[B][FONT=arial]not do:
**[SIZE=2][/SIZE]**[B][SIZE=2]echo export PYTHONPATH='$PYTHONPATH':/usr/lib/python2.7/virtGPIO >> ~/.bash_profile
source ~/.bash_profile[/SIZE][/B][B][SIZE=2]

if you have .profile in your "~/" don't do that....
 
Do this instead: 
echo export PYTHONPATH='$PYTHONPATH':/usr/lib/python2.7/virtGPIO >> ~/.profile
source ~/.profile

why the first will invalidate the "[/SIZE][/B][/FONT][/B][B][FONT=arial][B][SIZE=2]~/.profile" i guess....
[/SIZE][/B][/FONT][/B]

---

