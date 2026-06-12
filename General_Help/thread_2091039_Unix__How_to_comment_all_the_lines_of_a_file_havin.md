---
title: "Unix | How to comment all the lines of a file having a specific string"
date: 2012-12-04
forum: General Help
---

### Post by sarin_cv on 2012-12-04
Hi All,

I have a file like this

red 12345
12345 abc red
ddd red dfgd
abc blue 123
123 red123
123red123

I need to comment all lines from this file containing the string 'red'. Desired output.

#red 12345
#12345 abc red
#ddd red dfgd
abc blue 123
#123 red123
#123red123

How to achive this in Unix??
Thanks,
sarin

---

### Post by drmrgd on 2012-12-04
Try this (still learning perl, so maybe it's more clumsy than a pro would do):

```

#!/usr/bin/perl

use warnings;

while (<>) {
    foreach ($_) {
        if (/red/) {
            print "#" . $_;
        }
        else {
            print $_;
        }
    }
}

```

Then just run it like this:

```
name_of_script.pl <file_to_process>
```

---

### Post by Grenage on 2012-12-04
```
sed -i 's/\(.*red.*\)/#\1/' *FILENAME*
```

eg:

```
russellm@ubqd:~$ cat FILENAME
red 12345
12345 abc red
ddd red dfgd
abc blue 123
123 red123
123red123
```

```
russellm@ubqd:~$ sed -i 's/\(.*red.*\)/#\1/' FILENAME
russellm@ubqd:~$ cat FILENAME
#red 12345
#12345 abc red
#ddd red dfgd
abc blue 123
#123 red123
#123red123
```


I'm sure others will have better solutions.

---

### Post by sarin_cv on 2012-12-04
what is sed -i option for? 

using AIX Unix. It says illegal option '-i'

---

### Post by Grenage on 2012-12-04
> **sarin_cv said:**
> what is sed -i option for? 

using AIX Unix. It says illegal option '-i'

Ah, I'm guessing it does not support the in-line option (makes changes to the file directly).  You could however simply output to a new file:

```
sed 's/\(.*red.*\)/#\1/' FILENAME > NEWFILE
```

---

### Post by drmrgd on 2012-12-04
> **Grenage said:**
> ```
sed -i 's/\(.*red.*\)/#\1/' *FILENAME*
```

eg:

```
russellm@ubqd:~$ cat FILENAME
red 12345
12345 abc red
ddd red dfgd
abc blue 123
123 red123
123red123
```

```
russellm@ubqd:~$ sed -i 's/\(.*red.*\)/#\1/' FILENAME
russellm@ubqd:~$ cat FILENAME
#red 12345
#12345 abc red
#ddd red dfgd
abc blue 123
#123 red123
#123red123
```


I'm sure others will have better solutions.

I really ought to learn sed one of these days :D

---

### Post by Grenage on 2012-12-04
Likewise for perl and friends; your method is more elegant. :)

---

### Post by Vaphell on 2012-12-04
noobs :P
```
sed '/red/ s/.*/#&/'
sed '/red/ s/^/#/'

```

---

### Post by Grenage on 2012-12-04
> **Grenage said:**
> I'm sure others will have better solutions.

> **Vaphell said:**
> noobs :P

See, someone's always got a better way. ;)

---

### Post by drmrgd on 2012-12-04
> **Vaphell said:**
> noobs :P
```
sed '/red/ s/.*/#&/'
sed '/red/ s/^/#/'

```

Whoa!  Well, like I said, I really gotta learn sed it looks like!  Vaphell's saving me carpal tunnel one keystroke at a time it looks!

> Likewise for perl and friends; your method is more elegant.

Thanks for the compliment.  Not sure all that typing would be considered elegant though ;)

---

### Post by Vaphell on 2012-12-04
> Whoa! Well, like I said, I really gotta learn sed it looks like! Vaphell's saving me carpal tunnel one keystroke at a time it looks!
if you know perl you should know sed right off the bat, their expressions are pretty much the same.

*sed* and *perl -pe* are almost equivalent (-p assumes all that while(<>) boilerplate code)
```
sed '/red/ s/^/#/'
perl -pe '/red/ s/^/#/'
```

as a bonus: awk would be like this
```
awk '/red/ {print "#" $0; next; }{ print $0; }'
```

---

### Post by drmrgd on 2012-12-04
> **Vaphell said:**
> if you know perl you should know sed right off the bat, their expressions are pretty much the same.

*sed* and *perl -pe* are almost equivalent (-p assumes all that while(<>) boilerplate code)
```
sed '/red/ s/^/#/'
perl -pe '/red/ s/^/#/'
```

as a bonus: awk would be like this
```
awk '/red/ {print "#" $0; next; }{ print $0; }'
```

Ahhhh!  That's the missing part of the puzzle (for me), the -p option!  I originally tried to do a perl oneliner (although my substitution was still just as noobish), but couldn't figure out how to read the lines into an array quite right (hence the edit).  I didn't know about the -p option.  Thanks for the tip!

I've been force-feeding myself perl these days in order to learn it.  I need more puzzles like this :D

---

### Post by Cheesemill on 2012-12-04
[This]("http://shop.oreilly.com/product/9781565922259.do") book is well worth a read if you can find a copy, I've got it on loan from the library at the moment.

---

### Post by sarin_cv on 2012-12-06
Thank you all :) I'll definitely try your methods. In between, I also tried and arrived at a solution. Though it's not efficient as yours, it works for me. :)

file="$1"
bkpfile="$1.bkp_$$"
tmpfile="$1.tmp_$$"
IFS=""
# Read the input file line by line
while read line
do
  
    #Get the first character of the line 
    firstchar=`echo "$line" | tr -d '\t' | tr -d ' ' | cut -c1` 

    if [[ "x${firstchar}" != "x" &&  $firstchar = "#" ]]
    then
      echo "$line" >>  $tmpfile    
    else

    if [[ `echo $line | grep -ic "$traceon" ` -gt 0 || `echo $line | grep -ic "$traceoff" ` -gt 0 ]]
    then
      echo "#$line" >>  $tmpfile
    else
      echo "$line" >>  $tmpfile    
    fi
    fi
done <"$file"

---

