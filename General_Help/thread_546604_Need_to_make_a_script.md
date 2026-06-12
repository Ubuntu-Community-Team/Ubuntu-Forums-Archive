---
title: "Need to make a script"
date: 2007-09-09
forum: General Help
---

### Post by herbster on 2007-09-09
I use this often:

```
scp filename.jpg login@website.com:public_html
```

to upload files to my website, usually single files on my desktop and such.

I'd just like to not have to type the whole login@ part everytime. What would be a script that would prompt for the "filename.jpg" part and execute the command?

TIA! :)

---

### Post by tripokey on 2007-09-09
Hi!

Open your favourite editor and type:
```

#!/bin/bash
scp $1 login@website.com:public_html
exit 0

```

and save it to whatever file name you like.

after that you have to type ```
chmod u+x [the filename you have chosen]
```

now you can run your new command by typing:
```
./[the chosen filename] [filename.jpg]
```

---

### Post by Martje_001 on 2007-09-09
Hey tripokey,
does $1 mean 'first argument' of the script?

---

### Post by herbster on 2007-09-09
> **tripokey said:**
> Hi!

Open your favourite editor and type:
```

#!/bin/bash
scp $1 login@website.com:public_html
exit 0

```

and save it to whatever file name you like.

after that you have to type ```
chmod u+x [the filename you have chosen]
```

now you can run your new command by typing:
```
./[the chosen filename] [filename.jpg]
```

Holy crap that works like a charm, schweet! Thank you SO much tripokey!! Greatly appreciated :) :)

---

### Post by tripokey on 2007-09-09
Np.

> Hey tripokey,
does $1 mean 'first argument' of the script? 

Yes. and $0 is the command that was invoked and $# is the number of args used.

---

