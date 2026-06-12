---
title: "command line file colours"
date: 2017-05-27
forum: General Help
---

### Post by dannyk2 on 2017-05-27
Hello all, hope that i'm in the right section.
I can set the command line permissions no problem but what is getting to me are the different file colours and their meanings.
For example i created a really basic "Hello world" file with a .txt extension. Then i give the permissions to execute the file: 
```
chmod +x file_name.txt
``` but when i am at the prompt and in the correct directory i type: ./file_name.txt an error appears on the screen? The file in question is a light green colour. Thanks for any help or advice in advance.

---

### Post by vasa1 on 2017-05-27
> **dannyk2 said:**
> Hello all, hope that i'm in the right section.
I can set the command line permissions no problem but what is getting to me are the different file colours and their meanings.
For example i created a really basic "Hello world" file with a .txt extension. Then i give the permissions to execute the file: 
```
chmod +x file_name.txt
``` but when i am at the prompt and in the correct directory i type: ./file_name.txt an error appears on the screen? The file in question is a light green colour. Thanks for any help or advice in advance.
What are the contents of *file_name.txt*, and what is the error?

As for colors, try```
dircolors -p | grep 32
```
I get```

# 30=black 31=red 32=green 33=yellow 34=blue 35=magenta 36=cyan 37=white
EXEC 01;32
#.cmd 01;32 # executables (bright green)
#.exe 01;32
#.com 01;32
#.btm 01;32
#.bat 01;32
#.sh 01;32
#.csh 01;32

```on my system.

---

### Post by SeijiSensei on 2017-05-27
You can turn off colors in directory listings with "ls filespec --color=no".  You can make this permanent by adding the line
```
alias ls='ls --color=no'
```
to the file /home/user/.bashrc.  There are some other examples of ls aliases in that file. You could also assign the alias to another command string, say "lsnc" for "ls with no color":
```
alias lsnc='ls --color=no'
```

Make sure not to include spaces around the equals sign.

If you want a script to run from the command prompt with "./script_name", you must have a "hashbang" header like this:
```

#!/bin/bash

[rest of the script]

```
That tells the operating system what program to use to interpret the script.  It need not be bash.  Scripts in languages like perl or PHP have top lines that read:
```
#!/usr/bin/perl
```
or 
```
#!/usr/bin/php
```

---

