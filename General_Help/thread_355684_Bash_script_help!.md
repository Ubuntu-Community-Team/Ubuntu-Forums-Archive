---
title: "Bash script help!"
date: 2007-02-07
forum: General Help
---

### Post by rich.bradshaw on 2007-02-07
This is what I have for part of a script, I want to output the tranposed version of informationw${Z}.txt as information${Z}.txt, but information${Z}.txt ends up empty. Why?

```
Z=$START
while [ $Z -le $MAXVAL ] # Tranpose information files.
do

(for i in 4000;
do
   cat informationw${Z}.txt | awk "{print \$${i}}" | tr '\n' '\t'
   echo 
done) > information${Z}.txt

rm informationw${Z}.txt
Z=$((Z+5))
done
```

The key part is the loop. If I run this code without the redirect to information${Z}.txt, then it echos to the screen the transposed version, but trying to redirect it fails... any ideas?

Sure it is quite simple!

Rich

---

### Post by lloyd_b on 2007-02-07
Change ```
done) > information${Z}.txt
``` to ```
done) >> information${Z}.txt
```

The single ">" overwrites the file on each iteration.  Changing to double ">>" causes it to append to the end of the file instead.

Lloyd B.

---

### Post by rich.bradshaw on 2007-02-07
If I do that then all my information${Z}.txt files just contain 4000....

---

### Post by rich.bradshaw on 2007-02-07
Actually, they are still empty...

---

### Post by typhoongs on 2007-02-07
```
echo 
done) >> information${Z}.txt

``` i think >> is in wrong place , must be after echo like
echo >> information${Z}.txt

---

### Post by rich.bradshaw on 2007-02-07
That didn't work either....

This is annoying! It's got to be simple, everything else like this seems straightforward!

---

### Post by koenn on 2007-02-07
try something like
```

RESULT=$(

    for .... 

    done
)

echo $RESULT > information$Z.txt
```

or closer to the original (I also think the redirect is at the wrong place) - try something like


```
...
do
   ( cat informationw${Z}.txt | awk "{print \$${i}}" | tr '\n' '\t'  ) >> information$Z.txt

done
...

```
I don't know awk too well and don't fully understand your pipes so it might be > or >>

---

### Post by TyphoonJoe on 2007-02-07
Why not do this:

```
Z=$START
while [ $Z -le $MAXVAL ] # Tranpose information files.
do

(for i in 4000;
do
   cat informationw${Z}.txt | awk "{print \$${i}}" | tr '\n' '\t' >> information${Z}.txt
done)

rm informationw${Z}.txt
Z=$((Z+5))
done
```

No time to actually test for you, but Good Luck.

---

### Post by rich.bradshaw on 2007-02-07
None of these work....

Why not?????

This is silly!

Thanks for everyones suggestions!

---

### Post by lloyd_b on 2007-02-07
I misunderstood.  And come to think of it, I'm still confused.

Could you clarify what you're trying to do?  What I *think* you're trying to do is take a series files, each consisting of a single line of data, in the form:
```
one two three four five
```
and reverse them to produce
```
five four three two one
```

In which case your script shouldn't be working under any circumstances, as the 
```
for i in 4000
```
will iterate once per file, with a value of 4000.  I think you mean
```
for i in {1..4000}
```
which will iterate 4000 times per file, i=1, then i=2, i=3, etc.

Secondly, the "echo" inside of the loop will cause the results to be one entry per line:
```
five 
four
three
two
one
```

which sorta defeats the purpose of having the "tr" command.

So what I think you're looking for is
```
(for i = {1..4000};
do
     cat informationw${Z}.txt | awk "{print \$${i}}" | tr '\n' '\t'
done)
echo
```

If I'm misunderstanding the purpose of the script (which would be a far from uncommon occurrence:) ), then please provide some more details as to what the files look like to begin with, and what you want them to look like afterward.

Lloyd B.

---

### Post by rich.bradshaw on 2007-02-08
Theyare simply files with 4000 columns, and 100 rows. I want their to be 100 Columns and 4000 rows, so

```
a b c d ....
1 2 3 4 ...
7 8 9 0 ...
```

becomes

```
a 1 7
b 2 8
c 3 9
d 4 0
. . .
. . .
. . .
```

I was given the bulk of this script in this forum, and can verify that it works, but can't get it to save the results in a file...

---

### Post by lloyd_b on 2007-02-08
Okay, that helps a lot.

Here's a test I ran on my machine:

file "test1.dat"
```
a b c d
1 2 3 4
! @ # $
```

Script:
```
START=1
MAXVAL=1
Z=$START
while [ $Z -le $MAXVAL ] # Tranpose information files.
do

(for i in {1..4};
do
   cat test${Z}.dat | awk "{print \$${i}}" | tr '\n' '\t'
   echo
done) > result${Z}.dat

Z=$((Z+1))
done
```

Contents of output file "result1.dat"
```
a       1       !
b       2       @
c       3       #
d       4       $
```
I ran it against a set of 10 files, "test1.dat", "test2.dat", etc.  results are consistent for all 10 "result#.dat" files.

Is that what you were hoping for?  If so, then just changing the line
(```
for i in 4000;
```
to
```
(for i in {1..4000};
```

in your script should work.

I still don't see how this worked for you to begin with.  With the equivalent line of 
```
(for i in 4;
```
my output file looks like 
```
d       4       $
```
:confused: :confused: :confused: 

Lloyd B.

---

