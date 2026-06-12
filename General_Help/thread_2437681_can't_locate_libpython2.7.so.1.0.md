---
title: "can't locate libpython2.7.so.1.0"
date: 2020-02-27
forum: General Help
---

### Post by mprovitina on 2020-02-27
[SIZE=3][FONT=arial]I'm trying to install an application called Prism pipeline on Ubuntu 19.10. The installer fails with this error:

```
Traceback (most recent call last):
File "Scripts/PrismInstaller.py", line 65, in <module>
from PySide.QtCore import *
ImportError: libpython2.7.so.1.0: cannot open shared object file: No such file or directory
Traceback (most recent call last):
File "Scripts/PrismCore.py", line 68, in <module>
from PySide.QtCore import *
ImportError: libpython2.7.so.1.0: cannot open shared object file: No such file or directory

```

if I run locate l*ibpython2.7.so.1.0*, it gives me blank result indeed. if I just run pythonin my terminal, the Python session starts correctly with python 2.7.17, so I'll say that it's installed on my System (I think that's is the default installation that comes with ubuntu).[/FONT][/SIZE][SIZE=3][FONT=arial]So after a google research I found that I possibly need to install libpython2.7, but *sudo apt-get install libpython2.7 *results in:

[/FONT][/SIZE]
[SIZE=3][FONT=arial]```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libpython2.7 : Depends: libpython2.7-stdlib (= 2.7.17~rc1-1) but 2.7.17-1~19.10 is to be installed
E: Unable to correct problems, you have held broken packages.

```

How can I fix it? thanks in advance[/FONT][/SIZE]

---

### Post by deadflowr on 2020-02-27
[s]What have you added to the system outside of the normal repositories,
because it wants/needs to install a different version than what Ubuntu supplies.
> [I]libpython2.7-stdlib (= **2.7.17~rc1-1**) but **2.7.17-1~19.10** is to be installed
[/I]Ubuntu ships the **2.7.17-1~19.10 **version,
so I have no idea where the  **2.7.17~rc1-1** version is coming from...

Solve that and you should solve the problem.[/s]

**Edit:**

Oh, I see. You turned off the -updates repository at some point.
Open the program Software and Updates and go to the tab Updates.
enable  Recommended Updates.
Closing the program should reload the repository information, and then it should allow installing the correct package versions.

---

### Post by mörgæs on 2020-02-27
Help is already being provided:[URL="https://prism-pipeline.com/forum/topic/linux-installation-failing/#postid-1477"]
https://prism-pipeline.com/forum/topic/linux-installation-failing/#postid-1477[/URL]

---

### Post by mprovitina on 2020-02-28
> **mörgæs said:**
> Help is already being provided:[URL="https://prism-pipeline.com/forum/topic/linux-installation-failing/#postid-1477"]
https://prism-pipeline.com/forum/topic/linux-installation-failing/#postid-1477[/URL]

that post is mine actually :lolflag:
[SIZE=2][FONT=arial]We didn't find a solution, Richard just said that he's gonna test Ubuntu, meanwhile I was trying to figure out why there isn't any [COLOR=#444444]libpython2.7.so.1.0 in my computer, so that's why I posted also here.

Also, to reply to deadflowr[/COLOR][/FONT][/SIZE][COLOR=#000000][FONT=arial]: Yes I disabled all update infact, because some weeks ago we had a huge problem with all our workstations, and it seemed to be caused by some auto-updates. So had to format every workstation and disable all updates.[/FONT][/COLOR][SIZE=2][FONT=arial][COLOR=#000000]Is there some way to install the necessary packages manually?

P.S. I didn't mentioned but if it can help: I haven't installed anything python-related apart from Python3. So I have only the python packages which come with Ubuntu 19.10 minimal installation[/COLOR][/FONT][/SIZE]

---

### Post by monkeybrain20122 on 2020-02-28
> **mprovitina said:**
> [SIZE=2][FONT=arial][COLOR=#444444]
Also, to reply to deadflowr[/COLOR][/FONT][/SIZE][COLOR=#000000][FONT=arial]: Yes I disabled all update infact, because some weeks ago we had a huge problem with all our workstations, and it seemed to be caused by some auto-updates. So had to format every workstation and disable all updates.[/FONT][/COLOR][SIZE=2][FONT=arial][COLOR=#000000]Is there some way to install the necessary packages manually?
[/COLOR][/FONT][/SIZE]


You have to re-activate all your repositories to install the right package versions manually (instead of upgrading everything) It would be handy if you have synaptic installed.

---

### Post by mörgæs on 2020-02-29
> **mprovitina said:**
> that post is mine actually

I know. The reason I posted was that I found it less polite to ask for people's time both here and there.

---

