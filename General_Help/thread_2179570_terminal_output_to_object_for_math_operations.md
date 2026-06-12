---
title: "terminal output to object for math operations"
date: 2013-10-08
forum: General Help
---

### Post by twinturbotom on 2013-10-08
I parse files for certain lines I would like to perform math on.  To do this now I pass the output into a ruby terminal or a to a .csv file for me to work without outside of the terminal session that I'm already in.  

For example I have 2 files which each contain a line documenting the amount of time it took for some software to complete it's job.  I want to then make a ratio of the times so I can say "the second one took 3 times longer than the first".


I find the entries with the following:

```
$ find . -name *.sum | xargs -I {} grep -iH -A5 analysis\ statistics {} | grep -i total
./solver/beast.sum- Total:             2315 seconds
./solver/vm.sum- Total:             6615 seconds
```

From here I can parse out everything but the numbers or even make a .csv file... 

to just output numbers:
```
$ find . -name *.sum | xargs -I {} grep -i -A5 analysis\ statistics {} | grep -i total | sed 's/[^0-9]*//g'
2315
6615
```


BUT how can I go from here to doing some simple math on those numbers?  I tried crazyness like this:
```
$ find . -name *.sum | xargs -I {} grep -i -A5 analysis\ statistics {} | grep -i total | sed 's/[^0-9]*//g' | echo (( $1/$2 ))

```
but I know I'm not passing my lines as variables.  Any help or thoughts? I'm preferably looking for a simple one liner.

Thank you!

---

### Post by steeldriver on 2013-10-08
You could read them into an array maybe?

```
$ while read -r key val units; do mydata+=( "$val" ); done < <(find . -name '*.sum' -exec grep -iA5 'analysis statistics' {} + | grep -i 'total:')
```

Then
```

$ echo $(( ${mydata[1]}/${mydata[0]} ))
2

```
or if you need more precision
```

$ echo "scale=2; ${mydata[1]}/${mydata[0]}" | bc
2.85

```

If you want to get fancier, you could use an associative array, which would allow you to refer to the values using the filename as a key, e.g.

```

$ declare -A myAssocData
$ while read -r key val units; do myAssocData[${key%-?otal:}]="$val"; done < <(find . -name '*.sum' -exec grep -iA5 'analysis statistics' {} + | grep -i 'total:')
$ 
$ echo "scale=2; ${myAssocData[./file2.sum]}/${myAssocData[./file1.sum]}" | bc
2.85

```

---

### Post by Vaphell on 2013-10-08
assuming that after grep 'total' you get something like this:
```
$ echo $'Total: 2232 seconds \nTotal: 4565 seconds'
Total: 2232 seconds 
Total: 4565 seconds
```
you can divide these numbers with awk
```
$ echo $'Total: 2232 seconds \nTotal: 4565 seconds' | awk 'x{print x/$2} !x{x=$2}'
0.488938
```


that said, oneliners are overrated. Outside of simplest of cases, having a well written, maintainable script or a shell function is much better.

---

### Post by twinturbotom on 2013-10-09
steeldriver: Thank you for this.  I really like the associate array with file name key.  Lots of knowledge here for me to absorb!  I appreciate it!
vaphell: I really like the awk method, I was trying to do that but couldn't get it right.  Thank you!  I don't entirely understand your awk arguments.  Mind quickly walking me through them?  I've been playing with it now for 20 minutes and almost grasp it!  The reason I'm looking for 1 liners here is for flexibility, I often don't know what I'm searching for and how to manipulate it until I see it live.

---

### Post by Lars Noodén on 2013-10-09
An alternate method, espcially if you want more complex calculations, is to use a script to parse the data into tab-delimited text and then import it into a spreadsheet like LibreOffice Calc.  All that's needed is that the columns of data are separated by tabs and that the rows by new lines and the resulting file gets the extension .csv  After the import it is easy to work on the data and make any calculations you decide on, both now and later.  Using that method, it would be fairly easy to calculate standard deviation, standard error, and many other things.

---

### Post by twinturbotom on 2013-10-09
Lars, that's basically what I'm doing now but once in a while I want to make a few quick comparisons and figured a savvier command line ninja would know the way!  Thanks

---

### Post by Vaphell on 2013-10-09
this awk part works like this: for every line of input awk goes through all blocks of code optionally guarded by a condition.
Awk treats 0 and null value as false so if you put uninitialized variable as a condition it will skip the block until a non-zero value is set.
assuming format of 'total: <number> seconds' $2 is what you want

```
line 1:  x{print x/$2}  # skip because uninitialized x -> false
        !x{x=$2}        # execute because !x -> true, { save 2nd field of the current line as x }
line 2:  x{print x/$2}  # execute because x!=null/0 -> true { print x/(2nd field of the current line) }
        !x{x=$2}        # skip because !x -> false
```

---

### Post by twinturbotom on 2013-10-10
Vaphell - Thank you!  I almost grasp this; very helpful.  I'll play with it and awk a bit more.  

> Awk treats 0 and null value as false so if you put uninitialized  variable as a condition it will skip the block until a non-zero value is  set.
Great stuff there!

Looks like you
LINE 1:
 x{print x/$2} - skip this block and move to the next for line 1 as your calling for an x that hasn't been defined
!x{x=$2} - save x as the 2nd field of the current line, which is still the first line

LINE 2:
x{print x/$2} - first block can be evaluated as x/$2 exists
!x{x=$2} - I don't get why this doesn't just redefine x as the current $2.  I need to play with that more.  Is it the exclamation or can I not redefine the variable?

---

### Post by Lars Noodén on 2013-10-10
The first part of an awk statement is always a pattern to be evaluated.  You can think of the above two-statement awk script like this pseudo-code:

```

     if ( $x ) { print $x/$2 }; 
     if ( ! $x ) { $x=$2 };

```

The part before the braces { } can be any formula or regex pattern.  awk reads the input one line at a time, but the variables it has internally stay set while the whole file is processed.

---

### Post by twinturbotom on 2013-10-10
LARS, this is a very helpful explanation.  Thank you!

---

### Post by Vaphell on 2013-10-10
Blocks are tested and potentially executed in order and changes persist. That said, it doesn't even matter if in the 2nd iteration we enter the 2nd block, the result is printed already.
With that in mind the expression can be simplified further
```
echo $'Total: 2232 seconds \nTotal: 4565 seconds' | awk 'x{print x/$2}{x=$2}'
0.488938
```

---

