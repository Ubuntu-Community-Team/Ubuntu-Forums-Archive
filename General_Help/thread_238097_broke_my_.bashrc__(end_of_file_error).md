---
title: "broke my .bashrc ? (end of file error)"
date: 2006-08-17
forum: General Help
---

### Post by Cryonic on 2006-08-17
I just changed my .bashrc file to set the PYTHONPATH variable, but now it gives me the following error:

"bash: .bashrc: line 82: syntax error: unexpected end of file"

I only added the following lines, and left the rest of the script untouched:

# 17 Aug 2006 by jovv
# add own working dir for Python
export PYTHONPATH='/home/jovv/development/python'

The directory does exist, maybe it has something to do with hidden characters? But how do I see and remove those?

EDIT: maybe of some importance: I used gedit to edit the file

---

### Post by Lunar_Lamp on 2006-08-17
I presume the PYTHONPATH line you added is the 82nd line?

---

### Post by Cryonic on 2006-08-17
yes, that's correct

---

### Post by jazzgossen on 2006-08-17
I've encountered this problem, too. Try running "dos2unix .bashrc". I think dos2unix is in the package sysutils, but I'm not sure.

---

### Post by Cryonic on 2006-08-17
Ok, tried it, didn't work.
Nice utility package though, thanks, will come in handy sometime :)

EDIT: well, for now I just made a new .bashrc file that works. I might play around with some commands and options of the old one and learn a few tricks, nothing lost there :)

---

### Post by taurus on 2006-08-17
Try to break that into two lines:

```

PYTHONPATH="/home/jovv/development/python"
export PYTHONPATH

```

---

### Post by Cryonic on 2006-08-17
It works in the new file with the command on one line, but thanks for the suggestion anyway ;)

---

