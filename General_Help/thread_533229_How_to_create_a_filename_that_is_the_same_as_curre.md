---
title: "How to create a filename that is the same as current folder name"
date: 2007-08-23
forum: General Help
---

### Post by FDPOD on 2007-08-23
Hi

I'm going nuts .... ;-(
Can't find a good reference out there and being a nOOb doesn't really help either ... :-)

Is there an easy way to create a filename that is created out of the current folder name ?

so something like :
```

#!/bin/bash
createfile CURRENTFOLDERNAME.txt   
pwd > CURRENTFOLDERNAME.txt  
ls >> CURRENTFOLDERNAME.txt  

```

Tx
FD

---

### Post by yellowband on 2007-08-23
use ```
 touch 
``` to make a file

try something like

```
touch `pwd`
```

notice the backticks, not quotes. this tells the shell to execute whats in the ticks, and put the results in its place

---

### Post by FDPOD on 2007-08-24
Hmm,...
Sorry but I can't make use of the information you gave me :confused:

Let's say I have a structure: 
*[COLOR="Blue"]/media/FreeAgent%20Drive/mOVIES/WhateverFolder2007/WhateverFolder01[/COLOR]*

Then the pwd command would produce :
```
$pwd
/media/FreeAgent%20Drive/mOVIES/WhateverFolder2007/WhateverFolder01
```

What I would like to do is :
0.) right click in a folder and call the script file that creates :
1.) a file that is called **[COLOR="Blue"]WhateverFolder01.txt[/COLOR]** (.. in the folder I call  the script upon) , and ...
2.) have that filename being passed on to the next command line to be filled with the extra info about 
2a.) the path ([COLOR="Blue"]pwd > WhateverFolder01.txt[/COLOR]) and ..
2b.) the folder content ([COLOR="Blue"]ls >> WhateverFolder01.txt[/COLOR])

So I would kind of expect the script file to look something like:
```

#!/bin/bash
CUR_FOLD= `GetCurrentFoldername`
pwd > $CUR_FOLD+".txt"
ls >> $CUR_FOLD+".txt"

```

---

### Post by capink on 2007-08-24
```
pwd=`pwd`
touch `basename $pwd`
```

---

