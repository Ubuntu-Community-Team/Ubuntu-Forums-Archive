---
title: "gedit showing \n instead of making a line break"
date: 2007-03-09
forum: General Help
---

### Post by Chuwawa on 2007-03-09
Hello everybody,

I have a small problem with gedit.
I have a script file wich when opened by gedit is showing "\n" instead of making a proper line break. Thus it is nearly very hard to read it.

Has anybody an idea how I can make gedit understand what \n means.

---

### Post by Jmccaffrey on 2007-03-09
Id venture a guess that the file infact says '\n' in it instead of what was meant by \n.  An easy correction to this would be something like 
```
cat file.txt | perl -e "while <STDIN> { \$_ =~ s/\\\\n/\\n/g; print; }" > file.txt
```

---

### Post by Chuwawa on 2007-03-10
Hi Jmccaffrey,

thanks for the reply.

I copied the the code into the terminal and replaced file.txt with the correct file name. Did not work though. I got an error message:

syntax error at -e line 1, near "while <STDIN>"
syntax error at -e line 1, near "; }"
Execution of -e aborted due to compilation errors.

The code is kind of cryptic to me, so I have no clue how to correct the error.

---

### Post by fragos on 2007-03-10
Open up the file in Gedit and <Ctrl>h for replace.  In the find entry enter \\n and in the replace entry enter \n.  Then replace all.  In Gedit, \n only translates to to an end of line in find and replace.  Find and replace uses \ as an escape character and \n means end of line.  \\ means the character \.

---

### Post by Chuwawa on 2007-03-11
Worked perfectly,

thanks a lot.

---

### Post by fragos on 2007-03-11
You're welcome.  Replace \n is very handy for reformating text that gets chopped up by many email forwards.

---

