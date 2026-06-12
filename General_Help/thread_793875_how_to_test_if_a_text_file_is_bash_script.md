---
title: "how to test if a text file is bash script"
date: 2008-05-14
forum: General Help
---

### Post by elflord5 on 2008-05-14
hi all

i want to find all the bash script on the system
normally how do oeople test if a text file is bash script ?

thx

---

### Post by PmDematagoda on 2008-05-14
Usually you can tell bash scripts from normal files by the very first line which is normally:-
```
#! /bin/sh
```

---

### Post by elflord5 on 2008-05-14
hi thanks
so i should test very file for the first line ?
is there a quicker way ?
i know konquer the file manager can tell if a file is a bash shell or not
but dont knwo how it does it

---

### Post by hyper_ch on 2008-05-14
I normally use
```

#!/bin/bash
```
without space

---

### Post by bollix47 on 2008-05-14
Try using the file command to see if it will give you what you want.

```
file  nameoffile
```

---

### Post by elflord5 on 2008-05-14
thx i'll give it a try later
for the moment i have:

find / -type f -exec head -n 1 {} \; | awk '{if ($1 == "#!/bin/bash") print $1;}'

but using this method i lose hold of the file name that i actually found

any hint ?

---

### Post by bingoUV on 2008-05-14
In the exec clause of find, echo the {} as well as head it. Use -n for echo so that there is not new line between filename and head. In awk, look for the second token ($2) rather than $1.

---

