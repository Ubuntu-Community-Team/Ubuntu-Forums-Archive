---
title: "export from within shell doesn't work"
date: 2007-09-07
forum: General Help
---

### Post by surfer63 on 2007-09-07
tI'm trying to write  a script that does start a program, but before doing this it needs to set some environment variables, like

```
#!/bin/sh 

CWD="`(cd \"\`dirname \\\"$0\\\"\`\"; echo $PWD)`"
TOP="`dirname \"$CWD\"`"

export DYLD_LIBRARY_PATH="$TOP/lib"
export PATH="$CWD:$PATH"
export PANGO_RC_FILE="$TOP/etc/pango/pangorc"
export FONTCONFIG_PATH="$TOP/etc/fonts"
```
This does not work however. When I give the export commands on the command line, it does function.
Switching the first line of "code"  to #!/bin/bash doesn't work either.

I am using bash: from the environment.
```
BASH=/bin/bash 
```
This does not work however, even though other (startup) scripts running from /etc/init.d also use export commands and do work.
What am I doing wrong?

---

### Post by aJayRoo on 2007-09-07
Remember that when you run a script it runs in a sub shell, so any variables you set will only be available in that new shell and will not be available in the shell where you ran the script from. If you want the script to operate on the current shell and actually create those variables you will need to run the script with the 'source' command as in:
```
source scriptname
```
Have you completed your script yet? If you launch a program from within your script it will have access to those variables, however like I said before if you are just checking to see if that part works, those variables won't be available once the script ends but don't worry as they will be available to anything inside the script! Hope that helps!

EDIT: I just re-read and I'm not sure if I was clear, although I mentioned the 'source' command, I do not think you will need to use it in this case, as the program launched from within the script will have access to those variables.

---

### Post by surfer63 on 2007-09-07
YES, that did it (and yes, the man page also said that but I didn't realize that when reading it).

I tried a "set | grep -i <variable>" from within the script and it showed the correct values.

Thanks for your quick reply.
(Well, actually it means that my script is suffering from something else a little bit further on :(, but that's another analysis)

---

### Post by aJayRoo on 2007-09-07
Ok, glad you got it sorted (well, mostly sorted!) :)

---

