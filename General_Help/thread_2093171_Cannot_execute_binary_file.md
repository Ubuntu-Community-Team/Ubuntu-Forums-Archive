---
title: "Cannot execute binary file"
date: 2012-12-10
forum: General Help
---

### Post by Emris Echo on 2012-12-10
heyall today i wrote a very basic program, compiled it with chmod u+X whichn worked fine but when i try to execute the file i get "cannot execute binary file" error message if anyone know why or how i can fix it please let me know (im sure by the very nature of my question it is obvious i am a total noob to bash commands so please keep any descriptions or instructions as  basic as possible)
thnx in advance

---

### Post by mcduck on 2012-12-10
> **Emris Echo said:**
> heyall today i wrote a very basic program, compiled it with chmod u+X whichn worked fine but when i try to execute the file i get "cannot execute binary file" error message if anyone know why or how i can fix it please let me know (im sure by the very nature of my question it is obvious i am a total noob to bash commands so please keep any descriptions or instructions as  basic as possible)
thnx in advance

it's "*chmod u+x*", not "*chmod u+X*". (large X would set special execute permissions, and isn't useful in your case).

If that doesn't solve the issue, then please give us a bit more detail about the file, and how are you trying to execute it.

---

### Post by Sazhen86 on 2012-12-10
Hi

What language did you write your program in?  If it's a bash script, did you make the first line specify that you wanted to run it in bash?  The first line would look something like this:

#!/bin/bash

Hope that helps.  If not, can you post the program's source code?

---

### Post by Emris Echo on 2012-12-10
i tried using chmod u+x but i still got the error im just trying to display a string below is the code im using 

#!/bin/bash
 # declare STRING variable
 STRING=”Statement”
 #print variable on screen  
 echo $STRING
(try not to to spray milk from your nostrils we all started somewhere ;))

---

### Post by mcduck on 2012-12-10
That's interesting, since its a shell script, not  a binary file, so the error message you get would have to be about something else than the script itself or it's permissions.

How are you trying to execute it?

This should work from the directory where the script is located:
```
./yourscript.sh
```
or from anywhere:
```
/path/to/yourscript.sh
```

---

### Post by Sazhen86 on 2012-12-10
Can you run "file myscript.sh" and post the output?  The "file" utility displays the type of the file.  In the case of your script file, the output should be something like:

myscript.sh: Bourne-Again shell script, UTF-8 Unicode text executable

---

### Post by Emris Echo on 2012-12-10
So it turns after browsing the properties that the execute permission was not turned on anybody know why the default is to not allow you to execute your files and how to change that 
thnx again guys for your time

---

### Post by drmrgd on 2012-12-10
> **Emris Echo said:**
> So it turns after browsing the properties that the execute permission was not turned on anybody know why the default is to not allow you to execute your files and how to change that 
thnx again guys for your time

It would be a big security risk to just make any file that's generated executable.  So, by default, the user is responsible for determining that, not the system, and has to make the file executable themselves.  Further, there is more than just executable.  In Linux, you have the option to make the file executable by just the owner, the owner plus the owner's group, and the owner, the owner's group, and everyone else.  

So, it's a bit more complex than just simply making anything that looks like it could be a program or script to the system executable.

Perhaps this is a good starting point of information:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Sazhen86 on 2012-12-10
Also, it is possible to run a script in the current shell using the  "source" command (abbreviated to "." as it's used quite often).  In this case the script doesn't have to have the executable bit(s) set to on. 

The other difference here is that scripts executed using the "source" or "." commands are able to affect the environment variables in the current shell, whereas having the executable bit set will cause them to be run in another instance of the shell and any changes to environment variables will be lost when that shell exits.

Finally, you can execute a script in another instance of bash directly using "bash myscript.sh".  Again, the script does not need the executable bit(s) set on for this to work.

Hope that helps and I haven't confused you.

---

### Post by dcstar on 2012-12-11
> **Emris Echo said:**
> heyall today i wrote a very basic program, compiled it with chmod u+X which worked fine but when i try to execute the file i get "cannot execute binary file" error message
.....

Changing attributes of a file has nothing to do with "compiling".

Tell us **exactly** what you are doing.

---

