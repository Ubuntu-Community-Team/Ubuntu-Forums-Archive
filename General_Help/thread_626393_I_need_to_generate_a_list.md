---
title: "I need to generate a list"
date: 2007-11-29
forum: General Help
---

### Post by jimmy the saint on 2007-11-29
I need to generate a list that is output to a text file.  When I was using windows I used an application that worked essentially like a file renamer.  you essentially defined what the constant and variable portions of the list you want are and like magic, it generates a list.  I cant find a program like that for linux.  Is there a way to accomplish this?

---

### Post by mpierce on 2007-11-29
An example:

ls /home/mpierce/* > dir.txt

Would send all the output from the list command (ls) to the file dir.txt 

To see how to use it:
man ls

Hope this helps...

---

### Post by jimmy the saint on 2007-11-29
I appreciate the respnse, but I am not looking to list the contents of anything.  I would like to define the parameters and have a list generated.  For example
If I tell it to generate a list of APPLE with a nemerical suffix counting up from 1 to 100, it would generate a list APPLE1, APPLE2, APPLE3 and so on and so forth up to APPLE100.

---

### Post by Whiffle on 2007-11-29
bash scripting!! wee!!  Copy this into a text file, save it, chmod +x it, and then run it.

```

#!/bin/bash

N=0

while [ $N -le 100 ]
do
        echo "APPLE"$N
        N=$(($N+1))
done

```

---

### Post by smartbei on 2007-11-29
Well, here is one in Python:

```

import sys
if len(sys.argv) != 5:
	print "USAGE: python script.py <output filename> <prefix> <start range> <end range>"
	sys.exit()
temp, fn, px, sr, er = sys.argv
f = open(fn,"w")
for a in range(int(sr),int(er)+1):
	f.write(px+str(a)+"\n")
f.close()

```
Not at my Ubuntu computer now so I don't know if it works :D. Save as script.py and run using:
> 
python script.py <output filename> <prefix> <start range> <end range>


---

### Post by Whiffle on 2007-11-29
Oooh, one upped with python.  


I guess its time to go to bed, or learn python.  It probably wouldn't hurt to do both...

---

### Post by jimmy the saint on 2007-11-29
wow, thank you guys.  I have guess I need to start learning a little programming if I am going to be productive in linux!!  I can copy and paste what you folks wrote, but I have absolutely no idea what I'm looking at!!

---

### Post by smartbei on 2007-11-29
I just hope it works - I am at work now and don't have Python installed. Test please :D.

---

### Post by Whiffle on 2007-11-29
Heres a place to start with bash scripting:
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)


Oh and heres what I get when I run that python script:
```

andy@whiffle:~$ python script.py blah apple 0 100
USAGE: python script.py <output filename> <prefix> <start range> <end range>

```

---

### Post by Whiffle on 2007-11-29
and im bored...so i modified my bash script to do the same thing as the python one, without the input checking because i don't know how

```

#!/bin/bash
S=$3  #S is set to the third item on the input
N=$4  #S is set to the fourth item on the input

rm $1 # delete whatever $1, in our case, the filename.  keeps it from adding to an old file

while [ $S -le $N ] #while $S is less than $N...
do                          # do...
        echo $2$S >> $1  # output $s (which is our prefix) and $S (our count), back to back, to a new last line in the file, whose name is stored in $1
        S=$(($S+1)) # add one to counter
done    #QED

```


edit: commented!

---

### Post by smartbei on 2007-11-29
You know, the python script works quite well for me. Are you sure you ran it according to the usage instructions?

Try copying the code again - I edited it a minute or two after posting it since I saw an obvious mistake.

---

### Post by Whiffle on 2007-11-29
Yep, works now.

---

