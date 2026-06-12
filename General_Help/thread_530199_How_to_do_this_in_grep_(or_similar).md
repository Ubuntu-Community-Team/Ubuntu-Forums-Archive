---
title: "How to do this in grep (or similar)?"
date: 2007-08-20
forum: General Help
---

### Post by Pinnocchio on 2007-08-20
Hi

I have a script that's checking for the contents of the word in a line and if it exists it outputs the line to a temporary holding file.

cat inputfile.txt | grep "Morning" > tempoutputfile.txt

Here's the problem, I ONLY want the output file to be created if the word Morning is matched, if there is no word Morning I want no output to the tempoutputfile

The standard behaviour of GREP seems to be that if the match happens it outputs the correct line, however if there is no match it outputs a null and thereby deletes the contents of the existing tempoutputfile.txt

I'm obviously being pretty thick but I can't see a quick solution to this (also I've been awake for 20 odd hours so can't think straight anymore).  If anyone can suggest a command line (doesn't have to be grep but only want to use grep, awk, sed etc...please no python or other suggestions).

Please help before I end up kicking the Dog!!

---

### Post by vanadium on 2007-08-20
I do not exactly get what you want, but if you want the output of grep to append to an existing file, you use the >> redirector. Then, a line will be added to the existing file if it matches, nothing will be added (nor deleted) if there is no match.

---

### Post by Pinnocchio on 2007-08-20
Thanks but I don't want to do an append

The inputfile gets updated with external data.....and at some point usually at midday the Morning part of that data isn't included.

What I want to do is keep the last Morning data block

So in effect the input file could look like this

Morning 7 5 4 9
Afternoon 5 9 3 7
Evening 5 8 9 0

During the Morning the numbers may change and I want to keep the most recent data block

At midday the Morning part of the input file gets dropped (not in my control) and the file now looks like this

Afternoon 5 9 2 6
Evening 4 6 9 0

So what I want to do is keep updating the most recent Morning line into my outputfile and then when Morning get's dropped from the inputfile keep that last Morning data block

---

### Post by cwaldbieser on 2007-08-20
> **Pinnocchio said:**
> 
The standard behaviour of GREP seems to be that if the match happens it outputs the correct line, however if there is no match it outputs a null and thereby deletes the contents of the existing tempoutputfile.txt

This is actually the standard behavior of the shell when you use the ">" IO redirector.  It doesn't have anything to do with the "grep" program.  As vanadium noted, you can use the ">>" IO redirector if you want to append to a file instead of overwriting it.

The IO redirectors are processed before any of the commands, so as soon as bash (or sh, or ksh, or dash, or whatever shell you are using) sees "> somefile", it truncates somefile and opens it for writing.  This will implicitly create the file before grep has even had a chance to run.

If you don't want to create the file at all if there is no match, you will need to do something like the following interactive example:
```

$ linematch=$(grep 'pattern' searchfile)
$ if [ "$linematch" ] ; then echo $linematch > somefile; fi

```
Of course, you can put this into a script rather than doing it interactively.

---

### Post by lloyd_b on 2007-08-20
> **Pinnocchio said:**
> Hi

I have a script that's checking for the contents of the word in a line and if it exists it outputs the line to a temporary holding file.

cat inputfile.txt | grep "Morning" > tempoutputfile.txt

Here's the problem, I ONLY want the output file to be created if the word Morning is matched, if there is no word Morning I want no output to the tempoutputfile

The standard behaviour of GREP seems to be that if the match happens it outputs the correct line, however if there is no match it outputs a null and thereby deletes the contents of the existing tempoutputfile.txt

I'm obviously being pretty thick but I can't see a quick solution to this (also I've been awake for 20 odd hours so can't think straight anymore).  If anyone can suggest a command line (doesn't have to be grep but only want to use grep, awk, sed etc...please no python or other suggestions).

Please help before I end up kicking the Dog!!

I can't give you a single command line to do this, but here's a short script that accomplishes the trick:
```
#!/bin/bash
# Note the "backtics" in the following line (backtic is above the tab key on US keyboards).
TEMPVAR=`grep "Morning" inputfile.txt`

if !(test -z "$TEMPVAR"); then
     echo "$TEMPVAR" > tempoutputfile.txt
fi

```

Explanation:  Execute the "grep .." command, getting the result into a shell variable.  Then test the shell variable, and only execute the "echo..." command if it is not a zero-length (null) string.

Comment: 'cat inputfile.txt | grep "Morning"' and 'grep "Morning" inputfile.txt' do exactly the same thing.

Lloyd B.

P.S. - DON'T KICK THE DOG!

---

### Post by Pinnocchio on 2007-08-20
Thanks guys

I'll try that and if I'm still stuck I'll come back.

(Dog get's a walk!!)

---

### Post by Pinnocchio on 2007-08-20
Just to say thanks again....that sorted it.

Off to bed now.

---

