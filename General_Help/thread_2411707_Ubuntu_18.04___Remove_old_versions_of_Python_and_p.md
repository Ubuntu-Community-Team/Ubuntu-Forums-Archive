---
title: "Ubuntu 18.04 _ Remove old versions of Python and pip"
date: 2019-02-02
forum: General Help
---

### Post by carlo8 on 2019-02-02
Hi there, I recently updated from Ubuntu 16.04 to 18.04.
After the update, I only had python 3.6.7, which as I understand is the default version for the operative system. Then, I installed python 2.7 (version 2.7.15rc1, specifically), so I was expecting to have only these two versions installed.

1) Am I correct in saying that the 3.6.7 is the default version for Ubuntu 18.04? So, no matter what, this version is needed from the system, and should not be uninstalled?

2) As I said, I was expecting to have only python 3.6.7 and 2.7.15rc1 installed. However, after a search, I found these files:

```

[COLOR=#555555][FONT=Monaco]/snap/core/6130/usr/bin/python3.5: Python 3.5.2[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]/snap/core/6130/usr/bin/python3.5m: Python 3.5.2[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]/snap/core/6259/usr/bin/python3.5: Python 3.5.2[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]/snap/core/6259/usr/bin/python3.5m: Python 3.5.2[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]/snap/core/6350/usr/bin/python3.5: Python 3.5.2[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]/snap/core/6350/usr/bin/python3.5m: Python 3.5.2[/FONT][/COLOR]

```

are they relics from before the update? Are they system files? Can they be removed, and how?


3) If I use the command:

```

whereis pip

```

I get the output:
```

[COLOR=#555555][FONT=Monaco]/home/carlo/.local/bin/pip /home/carlo/.local/bin/pip2.7[/FONT][/COLOR]

```

which is almost surely from before the update (I did not delete the /home partition when updating to Ubuntu18.04).
But how can I uninstall it?
If I try:
```

[COLOR=#555555][FONT=Monaco]sudo apt-get remove python-pip[/FONT][/COLOR]

```
I obtain the result (something like this, my system is in Italian, I'm translating):
```

"python-pip" is not installed and cannot be removed

```
so, apt.-get is not finding the version of pip I want to remove from the /home folder. Same goes when using Synaptic, python-pip results not to be installed. How do I remove it?

Thanks in advance!

---

