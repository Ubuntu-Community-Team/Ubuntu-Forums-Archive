---
title: "need a more complicated cut command"
date: 2019-06-11
forum: General Help
---

### Post by Skaperen on 2019-06-11
i have a big file (millions of lines) that i need to cut 3 columns from.  these columns are separated by a variety of *different delimiters* plus i need them to be in a *different order* than the order they are in the big file.  this is *beyond* the capability of the _[FONT=courier new]cut[/FONT]_ command.  any suggestions?

Ubuntu 16.04.6 here.

---

### Post by kpatz on 2019-06-11
awk (mawk) is what I use for more complex file processing.  Or something like Perl or Python.

---

### Post by #&amp;thj^% on 2019-06-11
[https://www.folkstalk.com/2012/02/cut-command-in-unix-linux-examples.html](https://www.folkstalk.com/2012/02/cut-command-in-unix-linux-examples.html)
And: [https://www.geeksforgeeks.org/comm-command-in-linux-with-examples/](https://www.geeksforgeeks.org/comm-command-in-linux-with-examples/)
And one I use a lot: [https://kadekillary.work/post/cli-4-ds/](https://kadekillary.work/post/cli-4-ds/)

---

### Post by Skaperen on 2019-06-11
the geeksforgeeks site is badly programmed.  i'm getting ads overlying parts of article text and code.  i came up with an idea for something like cut or awk but with a language (the idea) more sophisticated than cut but simpler than awk code.  i'll make a prototype in Python and if people like it (or i need more speed) a version in C.

---

### Post by TheFu on 2019-06-11
I'd use perl - set it up as a filter so stdin and stdout are used.

```
#!/usr/bin/perl
use strict;
use warnings;

# read from stdin, 1 line at a time
while (<>){
    chomp;

   # this splits using a : delimiter, but you can match on multiple delimiters with a regex
    my @larray = split(/:/, $_);  

    # print the columns you want to keep to stdout
    print "$larray[0], $larray[5], $larray[6]\n";
}
```
This can parse a /etc/passwd file ...  Run with **./parse.pl /etc/passwd**  use or redirect or pipe the output where you need it.

Take the output from this and sort using any tool you like. I'd use **sort** unless there is a good reason not to.  You could throw that output into a DBMS and have it do the sorting. Sky is the limit.  If it is less than 2M records and each record is under 1K, I'd probably just add the columns into an array, then have perl output them in the desired sort order.  This is the kind of stuff perl was created to handle.  Sorting a column in perl is a 1-liner. Lots of examples on google.  If you need to run it more than once on huge files, I'd use the quicksort variant.  The built-in sort can do that.

Bet python, ruby and easily do the same thing.  I just had the perl code laying around.

---

### Post by Skaperen on 2019-06-12
the way i'm thinking about this is a command where the expression of what to do fits on the command line in what i think are typical cases.  the "language" of this expression is a new thing i thought up.  users of it would need to read up on how it is done much like reading up on [FONT=courier new]cut[/FONT] or [FONT=courier new]find[/FONT] or other commands unless they use them a lot.

---

### Post by &amp;wP*!) on 2019-06-12
Perl is historically perfect in such things. The beast can process file of any big size. But recent years processors have been so fast that Python would also be appropriate..

Back to reality - If you want to code in Perl: As an ex-Perl monk I recommend to disable input record separator (which is newline "\n") in UNIX-like sytems. In that case the speed-up is incredible:
```
$HoldTerm = $/;
$/ = undef;
open SYSIN, "file.txt" or die;
$fc =<SYSIN>;
close SYSIN;
$/ = $HoldTerm;
```
.. then process your text in $fc.

Disabling \n-interleaved file read speeds-up I/O dramatically. You slurp the file in one shot. Then regex runs in RAM (because $fc is stored in RAM) without waiting for I/O because file read happened before. 
With this technique you can process very big files like 500 MB within 1 minute.

I am fed up with Perl. Python is the future.

HTH.

---

### Post by Skaperen on 2019-06-13
i want to get the expression to reformat in one line, preferably quite short.  expressing such things in Perl or Python would be a struggle getting it into one line, and beyond 2 or 3 data items i don't see how that would even be possible.  so that's why i came up with my own little way to express how to cut up columns for output.  an example is (in single quotes like on a shell command) ':>:>6]^,>5[,>20@'
which would do 3 columns, the 1st between two : and output it 6 characters wide right justified, the 2nd between two , found from the start of each line 5 characters wide left justified, and the data up to the next , placed at column 20 in the output.  this would be the only command argument if reading stdin and writing stdout.

---

### Post by TheFu on 2019-06-13
> **Skaperen said:**
> i want to get the expression to reformat in one line, preferably quite short.  expressing such things in Perl or Python would be a struggle getting it into one line, and beyond 2 or 3 data items i don't see how that would even be possible.  so that's why i came up with my own little way to express how to cut up columns for output.  an example is (in single quotes like on a shell command) ':>:>6]^,>5[,>20@'
which would do 3 columns, the 1st between two : and output it 6 characters wide right justified, the 2nd between two , found from the start of each line 5 characters wide left justified, and the data up to the next , placed at column 20 in the output.  this would be the only command argument if reading stdin and writing stdout.

Those are new requirements, not mentioned in the OP.

Seems like the definition of *write-only code*.  In 5 yrs, when you come back, will you remember this syntax?  Will the next guy?  OTOH, bash has functions you could add to your shell. That would be 1 line to invoke.  Writing maintainable code is an important goal.

---

### Post by Skaperen on 2019-06-13
i am not trying to implement a command for each specific case, but rather, just one (or up to four) that can handle a variety of cases, more than [FONT=courier new]cut[/FONT] can.  the flexibility of ([FONT=courier new]g[/FONT])[FONT=courier new]awk[/FONT], [FONT=courier new]perl[/FONT], [FONT=courier new]python[/FONT], or any programming language is not the goal.

the new "language" (that this command gets as an argument) is still being developed, it can change again.  here are the notes i made today:```

input actions:

\ next character is only data
' everything to next ' is data but \ still works
" everything to next " is data but \ still works
+ move specified number of columns to right
- move specified number of columns to left
^ set position to front of input line
$ set position to end of input line
> find data to right
< find data to left
{ get input from specified number of columns on right
} get input from specified number of columns on left

data action:

_ match one or more white spaces (spaces, tabs) unless given as \_ or quoted

output actions:

! output from data
| output from input
] output is padded to specified width, justified right
[ output is padded to specified width, justified left
@ output is placed at specified position in output
```

it's designed with the idea of interpreting it character by character.  regular characters get collected into a string with _ being recorded in a special code (unless as \_ or quoted).  some actions use the data as a number and some others use it as a string to either be searched or to be output.  each time an action sets a position that position is pushed on a stack.  when an output action uses input, it pops 2 positions from the stack, pushes a copy of the newest one back onto the stack, maybe flips them to have them in order, and indexes the input line to get the input that it will output.  this is done on each line.

i want to also implement one that "compiles" the string ahead of time to see if it performs better.  the first implementation is being done in Python.  then maybe i'll do one in C.

---

### Post by Skaperen on 2019-06-13
i've changed it, already:```

input actions:

\ next character is only data
' everything to next ' is data but \ still works
" everything to next " is data but \ still works
+ move specified number of columns to right
- move specified number of columns to left
{ get input from N columns on right
} get input from N columns on left

search actions:

^ jump to far left then search to the right
$ jump to far right then search to the left
> search to the right
< search to the left

data action:

_ match one or more white spaces unless given as \_ or quoted

output actions:

! output from data
| output from input
[ output is padded to specified width (from data), justified right
] output is padded to specified width (from data), justified left
@ output is placed at specified position in output (not repeatable)

repeat action:

* repeat search or output N times, whichever follows
```

---

### Post by HermanAB on 2019-06-14
I think that you should start by calculating a checksum for each record, so that after you shuffled the data, you can verify that the records are still correct and that nothing ended up shifted to a different record.

---

### Post by Skaperen on 2019-06-14
maybe i don't understand, correctly, what you mean.  the checksum of an input record will not usually be the same as the cheksum of the output record, or other input records.  if duplicate input records were likely, saving outputs indexed by the input record checksum might save time, if the checksum is calculated very fast.

---

### Post by HermanAB on 2019-06-15
The danger is that things can subtly screw up due to unexpected errors/funny characters somewhere in the data file and you won't know it screwed up, until other people start to complain.  You said there are millions of records, so I think that the risk is large.

A simple checksum (just add all the bytes) of the relevant fields is independent of the order of the fields and could help to provide you with peace of mind.  You really should think how to filter the data, check for errors and verify that your output is correct.

---

### Post by Skaperen on 2019-06-15
the output can include text from the command that is not in the input file.  maybe i should go ahead and implement the first working prototype and provide that source code (it is in Python3) and you can see what it does and/or try it.

---

