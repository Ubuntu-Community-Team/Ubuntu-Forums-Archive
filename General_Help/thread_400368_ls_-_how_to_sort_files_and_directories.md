---
title: "ls - how to sort files and directories?"
date: 2007-04-03
forum: General Help
---

### Post by Hub-1 on 2007-04-03
I would like to know how to sort files and directories with "ls"
This was usually already pre-configured in the distributions I used previous to Ubuntu.
Unfortunately that's not the case in here, and I wasn't able to figure it out reading the man-page. 
Here's what I want to do with a "**ls -l**" or "**ls -la**":

1. List directories first: Uppercase - Alphabetically
2. followed by directories: Lowercase - Alphabetically
3. followed by files: Uppercase - Alphabetically
4. followed by files: Lowercase - Alphabetically

Can someone please help me out?

---

### Post by kevpatts on 2007-04-03
Not a very efficient way but you could create a script containing:
```
#!/bin/bash

ls -1aF | grep "^\.*[[:digit]]"
ls -1aF | grep "^\.*[A-Z]" | grep "\/" | sed "s/\///g"
ls -1aF | grep "^\.*[a-z]" | grep "\/" | sed "s/\///g"
ls -1aF | grep "^\.*[A-Z]" | grep -v "\/"
ls -1aF | grep "^\.*[a-z]" | grep -v "\/"
```

The "a" can removed so as not to display hidden files if you wish. Then chmod 770 the file and put it somewhere in your PATH environment variable to use it as a command.

---

### Post by Hub-1 on 2007-04-04
Thank you, but that doesn't look very pretty to be honest. Are there any built-in options in "ls" wich can do this? Or at least something similar?

---

### Post by Maestro23 on 2007-04-04
> **Hub-1 said:**
> Thank you, but that doesn't look very pretty to be honest. Are there any built-in options in "ls" wich can do this? Or at least something similar?

If you can't navigate thru the man page, this link may be of more help: [http://www.ncsa.uiuc.edu/UserInfo/Resources/Hardware/IBMp690/IBM/usr/share/man/info/en_US/a_doc_lib/cmds/aixcmds3/ls.htm](http://www.ncsa.uiuc.edu/UserInfo/Resources/Hardware/IBMp690/IBM/usr/share/man/info/en_US/a_doc_lib/cmds/aixcmds3/ls.htm)

Good luck.

---

### Post by Hub-1 on 2007-04-04
> **Maestro23 said:**
> If you can't navigate thru the man page, this link may be of more help: [http://www.ncsa.uiuc.edu/UserInfo/Resources/Hardware/IBMp690/IBM/usr/share/man/info/en_US/a_doc_lib/cmds/aixcmds3/ls.htm](http://www.ncsa.uiuc.edu/UserInfo/Resources/Hardware/IBMp690/IBM/usr/share/man/info/en_US/a_doc_lib/cmds/aixcmds3/ls.htm)

Good luck.

I don't know why you are pointing me to this man page - As I already said in my first post, I couldn't find the command options to do this, not that I can't read.

Sometimes distributions patch the command line tools with more functionality, and sometimes there is just not everything documented. So my question is, are there any undocumented options in "ls", or have overlooked something?

---

### Post by Interestedinthepenguin on 2007-11-03
Nice script, kevpatts.:)  

...but ```
:digit
``` should be ```
 :digit:
```.  

I love the script, but have one, small problem; the -F command doesn't apply to what appears to be the commands that use more than one pipe.  

Here's some of the output:
```

~$ ls2
2bs/
DELL-drivers-port
Desktop
Documents
Downloads
Firefox
Pictures

```

...The listings after 2bs/ are also directories, why don't they have the following '/'?

...Also:  Is it possible to still have ls's output colored?  I've been trying, but no luck.

Thanks.

---

### Post by Interestedinthepenguin on 2007-11-09
Oh, nevermind; I got it (as far as having a '/' to signify directories):

```

ls -F | grep "^\.*[[:digit:]]"
ls -F | grep "^\.*[A-Z]" | grep "\/"
ls -F | grep "^\.*[a-z]" | grep "\/"
ls -F | grep "^\.*[A-Z]" | grep -v "\/"
ls -F | grep "^\.*[a-z]" | grep -v "\/"

```

:)

---

