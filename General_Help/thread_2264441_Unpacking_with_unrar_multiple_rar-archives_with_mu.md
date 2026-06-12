---
title: "Unpacking with unrar: multiple rar-archives with multiple passwords"
date: 2015-02-07
forum: General Help
---

### Post by b-12-3838 on 2015-02-07
Hello everybody,  I want to unpack a couple of rar archived documents that have multiple passwords.  I usually do this in the terminal with the command:  

find '/home/USER/Dokumente' -name '*.rar' -execdir unrar x -p'PASSWORD' -o- -kb -y {} '*txt' '*.pdf' \;  

But in this case i only use one password.
  So lets say I want to include the 2 passwords '123' and 'abc' 

How does the syntax need to look like?
 -p'123' -p'abc'  
does not work  

Thanks in advance

---

### Post by b-12-3838 on 2015-02-13
still waiting for an answer.

Thanks in advance

---

### Post by steeldriver on 2015-02-13
not that familiar with unrar - do some archives have one password and some the other, or are they double-password protected?

---

### Post by b-12-3838 on 2015-02-16
They all have different passwords.

For example:

File1.rar with the password 123
FIle2.rar with the password 456
File3.rar with the password 789

i think i just need to find some kind of syntax to include the passwords '123', '456', '789' in one bash command. Then the unrar extractor tests all of the three passwords untill one matches.
And they are not double-password protected. Every rar file has got one password.

But i want to include it in this kind of bash command:

#This command extracts txt and pdf from all rar files found in one big directory with the password -p'PASSWORD'
#But i want to tell the bash command to try more than 1 password for extracting
find '/home/USER/documents' -name '*.rar' -execdir unrar x -p'PASSWORD' {} '*txt' '*.pdf' \;

Thanks for any help

---

### Post by Holger_Gehrke on 2015-02-16
As far as I can tell from either the manual page or the help unrar gives when called without parameters unrar does not have the kind of option you want. You'll have to do a bit of scripting to do what you want:
```

#!/bin/bash
unrar x -p'PASSWORD1' -o- -kb -y "$1" '*txt' '*.pdf' || unrar x -p'PASSWORD2' -o- -kb -y "$1" '*txt' '*.pdf' || unrar x -p'PASSWORD3' -o- -kb -y "$1" '*txt' '*.pdf'

```

What this does: it tries to unrar the file passed as first parameter with your options and the various passwords until it succeeds.

Put this in a file in a directory on your $PATH ("$HOME/bin" is good for stuff like this, if it exists it gets appended to $PATH by .profile) and make it executable. In your find command call this script instead of unrar.

---

### Post by b-12-3838 on 2015-02-19
Hi,

what I did know is this:

create new document -> unrarscript.sh 
then I opened, put the script in and saved it.
then i made it executable with sudo chmod +x unrarscript.sh

But I still dont know how to choose the correct syntax to use this script instead of unrar with my find command.

The folder looks like this at the moment:

Folders:
test1 (inside of it test1.rar with the password 123)
test2 (inside of it test2.rar with the password 321)
beneath the folders there is my executable unrarscript.sh 

now i want to extract them inside the folders

[[IMG]http://abload.de/thumb/abo3uxz.png[/IMG]]("http://abload.de/image.php?img=abo3uxz.png") [[IMG]http://abload.de/thumb/acaauoq.png[/IMG]]("http://abload.de/image.php?img=acaauoq.png")

---

