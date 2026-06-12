---
title: "How do I &quot;cat&quot; something specific?"
date: 2006-10-27
forum: General Help
---

### Post by newbie22 on 2006-10-27
Using the "cat" command.  How do I cat something specific?

Assume this is the content of a file:
```

red orange yellow
yellow green blue
blue purple red

```
How would I "cat" the 3rd word of line 2?

If "cat" cannot do it, is there another command that can?

---

### Post by aysiu on 2006-10-27
Can you explain in plain English what you're trying to do? Are you trying to delete the word *blue*?

---

### Post by marx2k on 2006-10-27
well, im a total first day noob... but reading through man pages i at least have a partial answer...

cat whatever.txt | grep -n 2

but as far as parsing using space as delimiters, im not sure how thats done

---

### Post by newbie22 on 2006-10-27
Huh, delete it?  No...  I do not know how you got that idea.

Using the "cat" command would print the entire content of a file.  I want it to print just the 3rd word of line 2.

EDIT:

marx2k is on the right track.  Except the "grep -n 2" would look for "2" as a keyword and print the line number the keyword "2" is on.

In my case, I am suppose to not know what keyword I am searching for.  Because the keyword is a variable.

---

### Post by aysiu on 2006-10-27
I don't see anything about isolating words: ```
CAT(1)                                                                User Commands                                                                CAT(1)

NAME
       cat - concatenate files and print on the standard output

SYNOPSIS
       cat [OPTION] [FILE]...

DESCRIPTION
       Concatenate FILE(s), or standard input, to standard output.

       -A, --show-all
              equivalent to -vET

       -b, --number-nonblank
              number nonblank output lines

       -e     equivalent to -vE

       -E, --show-ends
              display $ at end of each line

       -n, --number
              number all output lines

       -s, --squeeze-blank
              never more than one single blank line

       -t     equivalent to -vT

       -T, --show-tabs
              display TAB characters as ^I

       -u     (ignored)

       -v, --show-nonprinting
              use ^ and M- notation, except for LFD and TAB

       --help display this help and exit

       --version
              output version information and exit

       With no FILE, or when FILE is -, read standard input.

EXAMPLES
       cat f - g
              Output f&#8217;s contents, then standard input, then g&#8217;s contents.

       cat    Copy standard input to standard output.


```

---

### Post by David_T on 2006-10-27
```

awk '2 {print $3}' filename

```

---

### Post by newbie22 on 2006-10-27
Is there another command that might give me the result I am looking for then?

Or the idea the earlier user had, pipe the output of cat, then have something isolate a specific line number and word number.

---

### Post by David_T on 2006-10-27
Yes, this is what awk is for (see above).

> **newbie22 said:**
> Is there another command that might give me the result I am looking for then?

Or the idea the earlier user had, pipe the output of cat, then have something isolate a specific line number and word number.

---

### Post by IYY on 2006-10-27
The awk solution is nice, but not very easy to understand (mainly, it requires learning awk which is a bit trickier than most basic utilities). So, here is a solution that is less elegant, but simpler to understand:

```

cat file | tail -n 2 | head -n 1 | cut -d' ' -f 2
```

2 here is the line number. How does it work? Well, tail gives you the last 2 lines. Head gives you the first 1 line of those 2 lines. Cut, with a space delimiter and field number 2, gives you the second word.

---

### Post by newbie22 on 2006-10-27
awk looks nice.  But when I tried the 
```
awk '3 {print $2}' file
```
it did not work very well.  The "3" above has no effect.  Thus it printed the 2nd word of all the lines.  Would be nice if the "3" worked.

```
cat file | tail -n 2 | head -n 1 | cut -d' ' -f 2
```
This worked.  But would not if I add new lines in later use since it relies on truncating the last 2 line.  The code would have to be altered each time a new line is added.

Anyone have any more ideas?

---

### Post by IYY on 2006-10-27
> This worked. But would not if I add new lines in later use since it relies on truncating the last 2 line. The code would have to be altered each time a new line is added.

Anyone have any more ideas?

The point here that the 2 is the variable you change to select the line number you wish to isolate. Of course if you wanted to count from the top instead, you could just as easily have used

```
cat file | head -n 2 | tail -n 1 | cut -d' ' -f 2
```

---

### Post by marx2k on 2006-10-27
Works for me...
I dont know WHAT I was thinking with grep -n...

marx2k@UbuLappy:~$ cat file
one two three
three four five
six seven eight
marx2k@UbuLappy:~$ cat file | head -n 2 | tail -n 1 | cut -d' ' -f 2
four

---

### Post by marx2k on 2006-10-27
> **David_T said:**
> ```

awk '2 {print $3}' filename

```

With a file that containes:
one two three
three four five
six seven eight


the above code outputs:
marx2k@UbuLappy:~$ awk '2 {print $3}' file
three
five
eight


so basically the third word of each line.  This code would be valuable if there was an easy way to pipe a specific line number from a file into awk

There should be an easy way to do this, shouldnt there?

---

### Post by Sef on 2006-10-27
I am moving this thread since this is not an absolute beginner topic.

---

### Post by IYY on 2006-10-27
n/m

---

### Post by spectrum42 on 2006-10-27
> **newbie22 said:**
> Using the "cat" command.  How do I cat something specific?

Assume this is the content of a file:
```

red orange yellow
yellow green blue
blue purple red

```
How would I "cat" the 3rd word of line 2?

If "cat" cannot do it, is there another command that can?

How about this using awk?  It should print the 3rd word in the 2nd line, i.e. "blue". Change myfile.txt to whatever your file is called.
```

awk '{if (FNR==2) print $3}' myfile.txt

```

---

### Post by David_T on 2006-10-27
Sorry I guess I didn't test my solution very well.
Here's how you can get just a line number (say line 3):
```

sed -n '3 p' filename

```

So the whole thing would be (if you wanted to print word 2):
```

sed -n '3 p' filename | awk '{ print $2 }'

```

(edit:  spectrum42's awk-only solution is probably better since it only spawns one process, but for large files,
```

awk '{ if (FNR==2) { print $3; exit } }' filename

```
is faster, because it stops reading once the line is found.

---

