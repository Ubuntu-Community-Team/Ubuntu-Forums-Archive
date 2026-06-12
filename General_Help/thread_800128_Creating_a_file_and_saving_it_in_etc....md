---
title: "Creating a file and saving it in /etc...?"
date: 2008-05-19
forum: General Help
---

### Post by oserdavid on 2008-05-19
There is one alleged fix for Flash sound problem in Ubuntu Hardy Heron here

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

One of the things it suggests is creating a file "/etc/asound.conf" with specific content.

Being a more or less complete newbie - I find that I cannot simply drag a file called asound.conf into my /etc folder - because access is denied, no permissions.

Obviously, I guess I need to do it as root user. But I haven't got the faintest idea how to save a new file I have created on my desktop into my /etc folder via root or any other terminal (in fact, just in case I've lost the file I created, I've even forgotten how I created it in the first place... Old age)

Would somebody be kind enough to take me through creating a file with any old content, calling it asound.conf, and saving it in /etc, step by step, please? :confused:
David

---

### Post by geraldm on 2008-05-19
One editor is nano
create the file with the command "nano ~/Desktop/asound.conf"
use Control-g to get a helpful list of commands
use Control-x to exit the help.
Then type in the text.
use Control-o to write the file
exit the program.

OR: create the file in ~/Desktop/asound.conf with any text editor.
After that, copy it to the destination:
```

sudo cp ~/Desktop/asound.conf /etc/asound.conf

```


Gerald

---

### Post by kbuel on 2008-05-19
an easy way to create a file in /etc is with the following command:

```
gksudo gedit /etc/asound.conf
```

when you hit save, the file will be written to the etc directory with the name 'asound.conf'

---

### Post by -grubby on 2008-05-19
Or you could run :

```
gksudo nautilus
```, navigate to /etc, and drag the file in there

---

### Post by oserdavid on 2008-05-20
Thanks guys - that should do it!
David

---

