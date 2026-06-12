---
title: "How to make Nautilus script for compile and install"
date: 2006-08-17
forum: General Help
---

### Post by Oreo on 2006-08-17
Surely there must be a Nautilus script that will automate the common task:

Unarchive a tar installation file
Switch to that directory
./configure (sleep a short time)
make (wait a long time until done)
sudo make install
(enter password for you)

(Perhaps it would be better if the password could be entered by the user at the start of the script.)

I use a program that is being actively developed, so I do this daily before I can start work.
I've looked at the Nautilus script site and didn't see a way to easily adapt anything there to do this task. (I'm new to all this!)

Thanks,
Oreo Phil

---

### Post by rowanparker on 2006-08-20
I guess one could be made (if there wasn't one already).
Although each installation process isn't always the same and you'd have to make it deal with errors.

---

### Post by IYY on 2006-08-21
I don't know about a Nautilus script, but since I assume you'd like to see the output in the terminal, the best idea is to make a shell script
Suppose you keep your archive in **~/Desktop/program.tar**. Suppose that after extracting the archive, a folder gets created **~/Desktop/MyProgramName**. 

```

#!/bin/sh
tar -zxvf ~/Desktop/program.tar && ~/Desktop/MyProgramName/configure && ~/Desktop/MyProgramName/make && ~/Desktop/MyProgramName/make install
```

Then, save this, for example, as installProgram.sh and

```
chmod +x installProgram.sh
```


And to run the program,

sudo ./installProgram.sh

---

### Post by rowanparker on 2006-08-21
Although you'd need to make it accept an input for the program name and path, I do not know how to do that.

---

