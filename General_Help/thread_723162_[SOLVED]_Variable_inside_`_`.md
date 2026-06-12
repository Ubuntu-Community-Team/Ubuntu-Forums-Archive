---
title: "[SOLVED] Variable inside ` ` ?"
date: 2008-03-13
forum: General Help
---

### Post by lambono on 2008-03-13
Hi Guys, 

I can use the following code to test the size of two files 

```


#!/bin/bash

s1=`du file1 | cut -f1`
s2=`du file2 | cut -f1`

echo File size 1 is $s1 and File size 2 is $s2

if [ $s1 -lt $s2 ]
then
	echo S1 is smaller
else
	echo S1 is bigger
fi


```

How can I change it to use variables for the file names? 
eg 

```
#!/bin/bash

$var1 = file1
$var2 = file2

s1=`du $var1 | cut -f1`
s2=`du $var2 | cut -f1`

echo File size 1 is $s1 and File size 2 is $s2

if [ $s1 -lt $s2 ]
then
	echo S1 is smaller
else
	echo S1 is bigger
fi

```

Thanks a lot for your help!

---

### Post by lloyd_b on 2008-03-13
> **lambono said:**
> Hi Guys, 

I can use the following code to test the size of two files 

```


#!/bin/bash

s1=`du file1 | cut -f1`
s2=`du file2 | cut -f1`

echo File size 1 is $s1 and File size 2 is $s2

if [ $s1 -lt $s2 ]
then
	echo S1 is smaller
else
	echo S1 is bigger
fi


```

How can I change it to use variables for the file names? 
eg 

```
#!/bin/bash

$var1 = file1
$var2 = file2

s1=`du $var1 | cut -f1`
s2=`du $var2 | cut -f1`

echo File size 1 is $s1 and File size 2 is $s2

if [ $s1 -lt $s2 ]
then
	echo S1 is smaller
else
	echo S1 is bigger
fi

```

Thanks a lot for your help!

Two things wrong with your variable definitions:

1.  When on the left side of the equal sign, it's just "var1", not "$var1"
2.  Do *not* have any spaces around the equal sign.

So
```
var1=file1
var2=file2
```
should make the script work.

A couple of recommendations:  First, it's a good habit to enclose the value of such variables in quotation marks.  If there's a space in the value, it won't be correctly assigned without them.  Second, when passing values as parameters (as in the "du" examples), it's a good idea to wrap quotation marks around the variables.  Spaces in filenames can cause problems without the quotes.
```
var1="file1"
var2="file2"

s1=`du "$var1" | cut -f 1`
s2=`du "$var2" | cut -f 1`
```

Lloyd B.

---

### Post by dark_phantom on 2008-03-13
I agree with lloyd_b's suggestions.  And if you like to input two files to compare other files dynamically and not static like you have it do this.

```

#!/bin/bash

var1=$1
var2=$2

s1=`du $var1 | cut -f1`
s2=`du $var2 | cut -f1`

echo File size 1 is $s1 and File size 2 is $s2

if [ $s1 -lt $s2 ]
then
	echo $var1 is smaller
else
	echo $var1 is bigger
fi


```

Then execute your script like "script file1 file2" and it will say which if file1 is smaller or bigger.

---

### Post by lambono on 2008-03-13
Great,
It is always the silly mistakes that get me! 
Thanks very  much for the replies. They do exactly what i wanted.
Cheers! 

Lambono

---

### Post by ghostdog74 on 2008-03-13
if you are just comparing size of 2 files, here's a shorter way
```

# du file1 file2 | sort -n -k1 |tail -1

```
the result will be the bigger file.

---

