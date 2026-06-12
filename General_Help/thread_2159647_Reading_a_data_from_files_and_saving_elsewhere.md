---
title: "Reading a data from files and saving elsewhere"
date: 2013-07-03
forum: General Help
---

### Post by sd@ksu on 2013-07-03
Guys, I have a list of files, say, 001.dat to 099.dat. First 3 lines of each file should not be considered. From next, the data is in two columns, X and Y column. What I want is following:
From each file, find the value of X and Y corresponding to the two maximum values of Y. Then save those values in another file in columns of: File name, X1, Y1, X2, Y2, Y3 where Y3=(Y1+Y2)/2.
may I ask your help in doing that?

---

### Post by Vaphell on 2013-07-04
```
for f in *.dat
do
  sed -n '4,$p' "$f" | sort -k2nr | awk -v f="$f" 'NR<3{ x[NR]=$1; y[NR]=$2; }
                                                   END { printf( "%s %g %g %g %g %g\n", f, x[1], y[1], x[2], y[2], (y[1]+y[2])/2 ); }'
done > results.txt
```

---

### Post by sd@ksu on 2013-07-04
Dear Vaphell: Thanks for your reply. The code does something (I am using it like a black box!) but does not give correct answers

---

### Post by Vaphell on 2013-07-04
give a sample of input data then and the expected result because it works on my test files
```
$ cat 001.txt
1...
2...
3...
10 22
23 154
33 35
3  12
3  124
5  **1267**
6  35
7  357
8   **732**

$ cat 002.txt
1 9999
2 9999
3 9999
10 2
23 14
33 3
3  1
3  14
5  **167**
6  3
7  **37**
8   32

$ for f in *.txt
> do
>   sed -n '4,$p' "$f" | sort -k2nr | awk -v f="$f" 'NR<3{ x[NR]=$1; y[NR]=$2; }
>                                                    END { printf( "%s %g %g %g %g %g\n", f, x[1], y[1], x[2], y[2], (y[1]+y[2])/2 ); }'
> done
001.txt 5 1267 8 732 999.5
002.txt 5 167 7 37 102
```

---

### Post by sd@ksu on 2013-07-04
I have uploaded two files here:
[http://ubuntuone.com/5DZi50gEgX6i2xD3K813vQ](http://ubuntuone.com/5DZi50gEgX6i2xD3K813vQ)
[http://ubuntuone.com/1Ipb7oP2LK0l8AmIwIo2Nq](http://ubuntuone.com/1Ipb7oP2LK0l8AmIwIo2Nq)

One thing I said wrongly in my first post, that, the first FOUR lines should be omitted. but i have tried your code by manually deleting one line from top but it still does not work on my system for some reason. May be, it has something to do with the way the data is displayed. Please see if something could be done about it. Thanks a lot Vaphell.

---

### Post by steeldriver on 2013-07-04
I think the difference is you didn't specify that the values to be sorted would be in scientific notation - Until Vaphell checks back in, I might suggest changing 

```
sort -k2nr
```

to 

```
sort -k2[COLOR=#0000ff]**g**[/COLOR]r
```

See if that works - also no need to delete the first line, just change 4,$ to 5,$ in the sed range

---

### Post by sd@ksu on 2013-07-05
Sure, I shall try that. I think that would work . I see what you mean. Thanks steeldriver. :-)
.
PS: When I said manually deleting one line from top, I did not put it correctly. I meant deleting one line from top in the data file, not the code.

---

### Post by sd@ksu on 2013-07-05
Thanks to you both, the code works!!! I have changed it to the following ( for displaying in scientific notation and also preserving the number of significant digits in my calculation:


> 
for f in *.chi
do
  sed -n '5,$p' "$f" | sort -k2gr | awk -v f="$f" 'NR<4{ x[NR]=$1; y[NR]=$2; }
                                                   END { printf( "%s %e %e %e %e %e\n", f, x[1], y[1], x[2], y[2], (y[1]+y[2])/2 ); }'
done > results.txt


It displays the results correctly. Thanks to both of you for saving so much of my time. I should improve my scripting skills!!
For the calculation part of "(y[1]+y[2]/)/2", do you think the number displayed is correct? I mean, considering the number of significant figures...it seems ok to me and hopefully am not missing anything elementary here.

---

### Post by sd@ksu on 2013-07-05
How do I mark this as solved?

---

### Post by Vaphell on 2013-07-06
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

btw you should have left the NR<3 as it was. Sed is where the header lines are removed. NR<3 in awk is for reading top 2 results from the sorted list (row 1 and 2). NR<4 means you read 3 top results but x[3] and y[3] are not used anywhere, so the code still works fine, just does one completely useless step.

sed: remove header lines -> sort: numeric sort in descending order -> awk: get top 2 results and do stuff with them

---

