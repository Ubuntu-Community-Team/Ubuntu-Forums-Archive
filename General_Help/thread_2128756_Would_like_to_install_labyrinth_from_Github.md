---
title: "Would like to install labyrinth from Github"
date: 2013-03-24
forum: General Help
---

### Post by thorbs on 2013-03-24
I would like to install the mind mappring software from Github [https://github.com/labyrinth-team/labyrinth/zipball/0.6](https://github.com/labyrinth-team/labyrinth/zipball/0.6)

I have actually succeeded once before, but can not remember how I did it. Can anybody help?

I am aware that 4.0 is in the ubuntu repositories, but the progress is significant so I would really like the latest. Anybody who can help?

---

### Post by zero2xiii on 2013-03-24
Hay,

The read me file supplies all the needed info:

> From the top directory of the package, run the command::

    ./labyrinth

You can also install Labyrinth with ``python setup.py install``, and
``./install_data_files.sh`` for icons and translations. It can then be run as
``labyrinth``.

If you have a specific issue, please ask that rather for a better helpful answer.

Cheers

---

### Post by thorbs on 2013-03-27
Hi I read the installation instructions. As far as I understand them is,

Open terminal

Move to the folder 

type comment python setup.py install

And hit enter 

That does not get me the result 

The other instruction I understand as 

Open terminal

Move to the folder 

type comment ./labyrinth

And hit enter 

That does not give any result either.

So I must not be able to understand how to use the install instructions.

t.

---

### Post by andrew.46 on 2013-03-27
Is there an error message when you type:
```

./labyrinth
```

from the source directory? Bear in mind there are some requirements:

```

Requirements
------------

* Python >= 2.6
* gtk+
* pygtk
* pygobject
* pycairo
* PyXDG

```

---

### Post by thorbs on 2013-03-27
Hi I have not installed any extra, so I might possibly be missing some of the requirements. 

The error I get is

Traceback (most recent call last):
  File "./labyrinth", line 35, in <module>
    from labyrinth_lib import utils
  File "/home/thorbjrn/Downloads/labyrinth/labyrinth_lib/utils.py", line 30, in <module>
    from numpy import array
ImportError: No module named numpy

---

