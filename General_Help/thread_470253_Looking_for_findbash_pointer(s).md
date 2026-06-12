---
title: "Looking for find/bash pointer(s)"
date: 2007-06-10
forum: General Help
---

### Post by arsenic23 on 2007-06-10
Ok, I want to take the results of a find command and get the total of all of the file's sizes.  Unfortunately I have no idea how to go about doing that, nor have I been able to find a good reference to help myself.

Basically what I want to eventually be able to do is take the results of ```
find -type f -ctime -1
``` and total the filesizes, and then move on to -ctime -2, -3, -4 etc.  Can anyone give me a hand or point me to a resource that might help?

---

### Post by kidders on 2007-06-12
Hi there,

> **arsenic23 said:**
> Can anyone give me a hand or point me to a resource that might help?The man pages are always a good place to start ... for instance, it turns out that **find** can do quite a lot with files it matches.

Sticking with your approach, you could try...```
find -type f -ctime -1 -printf '%s '
```
That would generate a long list of space-delimited numbers, that you could then just add up. To make the process slightly more robust, you could strip error messages out of **find**'s output this way...```
find -type f -ctime -1 -printf '%s ' 2>/dev/null
```The kinds of errors you might expect would be things like "Cannot stat..." (if you deleted a file at *precisely* the wrong moment!) or "Permission denied" (if **find** tried to descend into a directory you didn't have access to). Naturally, they would screw up any maths you tried to do.

Two additional suggestions (if you're using **find** in a shell script):

You can use **find**'s exit status to determine how accurate your totals are...

```
find -type f -ctime -1 ...
EXITCODE=$?

...
...

if [ $EXITCODE -eq 0 ]; then
     echo "Total: $TOTAL"
else
     echo "Total: $TOTAL (approx)"
fi
```

The idea is that if your **find** command encounters errors, the sum total will probably only be approximate.

My other suggestion is to consider re-thinking your approach a little. Something like ...```
for i in $(seq 7); do find -type f -ctime $i ...; done
```... could be a little inefficient, especially if you're scanning a large number of files. It would be a lot more fiddly to get right, but I imagine that performing a single pass for all files matching your entire "ctime" range would be significantly faster. The individual calculations would then only be a matter of separating out the right lines of stdout (or maybe a temporary text file), rather than having to rescan ... well ... possibly an entire filesystem.

---

### Post by arsenic23 on 2007-06-15
Thank you so much.  That was horribly helpfull.  I had read over the find man, but missing the point of -printf, I'd skipped its section.

I'm currantly using something along the lines of 
```
for b in $(seq 31); do i=-$b; echo ""; echo "*****$b*****"; find -type f -ctime $i -printf '%s '; done; echo ""
```
to display something I can read and interpret, but I still haven't found a way to total the results of the find, nor have I found a good no BS guide to bash scripting.

Well, anyway, thanks again.

---

### Post by kidders on 2007-06-15
No problem. :-)

I suppose one way of adding up lists of numbers would be something along the lines of...```
LIST="10 20 30"
TOTAL=0
for i in $LIST; do
     TOTAL=$(($TOTAL+$i))
done

echo $TOTAL
```... but since your lists are likely to be quite big, finding *efficient* ways of doing it might be worth a little examination.

> **arsenic23 said:**
> ```
for b in $(seq 31); do i=-$b; echo ""; echo "*****$b*****"; find -type f -ctime $i -printf '%s '; done; echo ""
```Executing an almost identical "find" 31 times certainly seems mind-blowingly inefficient. Tinkering around with some alternatives would definitely be worth it here.



I can't say I've ever come across any definitive sources on Bash scripting. After all, Bash is only one shell ... and people have many different approaches to doing the same things in it. Personally, I tend to go looking for stuff on a need-to-know basis ... where the answers I want come from don't often make a huge amount of difference to me. :-( Sorry I can't be more helpful on that one. You do have to be on the look-out for crap though ... although you seem to have noticed that already.

---

### Post by arsenic23 on 2007-06-15
Thanks again, you've been really helpfull.

Just to let you know, I'm not terribly worried about being efficient because I only need to run this in three of my media folders:
~/ext3/Comics\ Archived
~/img
~/Music

So far the results are pretty much instant.
Thanks again for your help.

---

### Post by stylishpants on 2007-06-15
You can use awk to do this kind of summing operation:

```
for i in $(seq 31); do echo -n "$i:"; find . -type f -ctime -$i -ls  | awk 'BEGIN{sum=0} {sum += $7} END{print sum}'; done

```

---

### Post by kidders on 2007-06-16
> **stylishpants said:**
> You can use awk to do this kind of summing operationKewl, thanks for that. :-) (I'm a bit scared of awk hehe!)

---

### Post by arsenic23 on 2007-06-19
Ok, I need a hand again if anyone would care to point one or two things out to me.

First off, I'm trying to make a script that reads for lines in all the files in a directory and then assembles them all nice and labled in a file on my desktop. ::
```
#!bin/bash

read lookin;
(i=`ls`; 
for a in $i; do echo "  file:" $a " "; cat -n $a | grep $lookin
done
) > "/home/arsenic23/Desktop/"$lookin".txt"
```
 The script I made works, but there is one or two little things I need to tweak ot make the output file the way I want it.  **note I've replaced my real user name with my handle on these forums.*

First off I wanted to write the files to ~/Desktop - but ~/ causes errors.  Whats the best way to put the active username in a variable?

I'd also like to have the file name $directoryname"-"$looking".txt", but I don't know how I should put the name of the current directory in a variable either.

The other thing is this:  Currantly I run the script and then it drops down a line and waits for me to input through read.  Is there a simple way to make is so I can just type the script and then put what I want after it instead of below it?

If anyone could give me a hand with even one of these things it'd be horrible helpfull.

---

### Post by kidders on 2007-06-19
Hi again,

Here are some suggestions. Stylishpants might have some alternatives for you too ... there are lots and lots of ways of doing most things in shell scripts. :-)

```
#!/bin/bash
echo $2 $3 $0 $1
echo "My name is `whoami`"
echo "The current directory is `pwd`"
```If you were to save that as /usr/local/bin/this, maybe...
```
$ this is very interesting
very interesting this is
My name is kidders
The current directory is /home/kidders
```

---

### Post by stylishpants on 2007-06-28
A few notes:

-Your username is already in the environment var $USER.  You can see all the environment vars already defined for you by typing "env".

-The command-line arguments to your script are found in an environment var called $@.  You can access them like this:

```

#!/bin/bash
for i in $@;
do
    echo $i
done

```

-Environment vars will get expanded inside double quotes.  This means that instead of this:
    echo "  file:" $a " ";
You can use this:
    echo "  file:$a ";    # more readable
It's only single quotes that will prevent expansion of $variables.

-This is known as a [UUOC (useless use of cat ]("http://partmaps.org/era/unix/award.html#cat")):
    cat -n $a | grep $lookin
You can just use grep alone instead:
  grep $lookin $a


Finally, if I understand your script correctly, I think you can do the same thing with a single command:

```
 perl -e 'for (@ARGV) { `grep -H $_ * > ~/Desktop/$_.txt` }' search_term_1 search_term_2
```

Define as many search terms as you like, it doesn't have to be 2.

---

### Post by arsenic23 on 2007-07-01
Thanks so much for your help again guys.

---

