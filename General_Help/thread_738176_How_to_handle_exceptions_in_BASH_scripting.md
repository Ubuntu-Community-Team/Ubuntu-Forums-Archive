---
title: "How to handle exceptions in BASH scripting?"
date: 2008-03-28
forum: General Help
---

### Post by hardcore_Ehb on 2008-03-28
Greettings,

I would like to know if is it possible to know when a command did not executed successfuly in a BASH script ?  Something like ExceptionHandling.
I would like my script to run an alternative command if some command returns an error.


Best Regards

---

### Post by justleen on 2008-03-28
let the command create output to /tmp/output

then do a test for that file

if [ -f $outputfile ] do;


for example...

or, in case of errors, redirect the error output
command 2>  /tmp/error

and test for that file

---

### Post by hardcore_Ehb on 2008-03-28
> **justleen said:**
> let the command create output to /tmp/output

then do a test for that file

if [ -f $outputfile ] do;


for example...

or, in case of errors, redirect the error output
command 2>  /tmp/error

and test for that file

I tried this but the file is still being created anyway.
 I did the following

ls non_existent_directory 2> /tmp/error
**Result:**
/tmp/error is created with error message "*ls: non_existent_directory: No such file or directory*"

Then I tried 
ls non_existent_directory > /tmp/error
**Result:**
Displays error *"ls: non_existent_directory: No such file or directory"* ,  and creates an empty /tmp/error file

Regards

---

### Post by ruibernardo on 2008-03-28
You can by knowing which error is returned by the command with $?:

```
$ mkdir test/
$ MYERROR=$?
$ echo $MYERROR
0
$ mkdir test/
mkdir: cannot create directory `test/': File exists
$ MYERROR=$?
$ echo $MYERROR
1
```

---

### Post by hardcore_Ehb on 2008-04-02
> **epimeteo said:**
> You can by knowing which error is returned by the command with $?:

```
$ mkdir test/
$ MYERROR=$?
$ echo $MYERROR
0
$ mkdir test/
mkdir: cannot create directory `test/': File exists
$ MYERROR=$?
$ echo $MYERROR
1
```

Hi,

First of all , my sincere apologizes for delaying in replying ,  I have been facing network problems.

I got your point and it is a nice idea . What if I want it to perform an action when a error ocurres ? Would I have to put a conditional statement after each command ? 
eg.

```
ls /non_existent_directory
if [  $? != "0" ] ; then
echo "ERROR"
fi
```

Does Linux have a way to tell us if something goes wrong in a script ?
Is not there any variable that keeps track  of erros in a script ?

The only solution I can see so far is creating a function , but I would like to know if there is not an easier way .


Regards

---

