---
title: "Sending output of find / grep to a txt file - Getting errors"
date: 2017-07-23
forum: General Help
---

### Post by Alan5127 on 2017-07-23
Hi All,

I have client that has a load of informational / instructional videos for their products (thousands accumulated over the years).

They asked me if I knew of a way to find the ones with the lowest resolutions, so that they can match to product sales and thus prioritise updating / re-recording them in HD.

I said 'no problem!', which it was, so I ran the following command from the top level of the network drive that contains the videos (I actually made a copy of the entire directory and sub-directories and used that due to me being a coward):

```
find . -type f -print0 | xargs -0 mediainfo | grep -e "Complete name" -e "Width"
```

This works as expected, giving me two lines for each video (filename and the 'width' - I can also look for the 'height' or whatever else I like, but it doesn't matter to my question).  I can copy / paste that into Libre Calc, and sort in there - no problem.

However, I didn't like getting the results to the screen, so I did this instead:

```
find . -type f -print0 | xargs -0 mediainfo | grep -e "Complete name" -e "Width" > 0000.txt
```

Now it gets interesting.  This outputs a load of error lines to the screen showing:

```
E: File read error
```

which goes on for some time (there are thousands of videos across many sub-directories), but eventually it finishes, and leaves a file (0000.txt) in the directory that is exactly what I want.


*Question*

Why am I getting the error lines (albeit that they don't seem to cause an actual problem in the txt file), and what do I need to change in the command to stop that happening?


Thanks,

Alan.

---

### Post by SeijiSensei on 2017-07-24
You can stop the errors from appearing on the console by adding
```
2>/dev/null
```
to the end of the command.  The errors are sent to the "syserr" device which is represented by the "2" in the code above.

I think the error comes from this part of the command
```
grep -e "Complete name" -e "Width"
```
If you're looking for a line with both "Complete name" followed by "Width" later on you can use the regular expression
```
grep -e "Complete name.*Width"
```
or you can use another pipe to grep
```
grep -e "Complete name" | grep -e "Width"
```

---

### Post by btindie on 2017-07-24
The issue with your above script is that it would split the details for each file over two lines.

One way around it is to create a temporary script to process the media info which would also include the filename on the same line, similar to grep output.

getwidth:
```

mediainfo "$1" | grep -E '^(Complete name|Width)[ ]+' | awk -F: '{sub(/^[ ]+/,"",$2);print $2}' | paste -sd:

```

And run as:
```

find . -type f -exec /path/to/getwidth '{}' \; 2>/dev/null

```

The File read error may be because the file isn't understood by mediainfo. So you may want to extend the getwidth script to first test that the file being queried is recognised by mediainfo.

---

### Post by TheFu on 2017-07-24
"syserr" is a new term for me.  I've always heard and seen "stderr".  Are those the same?
"stdout" is what normally is redirected to files (or piped).  It is common to redirect stderr into stdout to have a full log of the program output.

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html) explains all about redirection.

FD 1 (file descriptor) is always stdout in bash and most other shells.
FD 2 is always stderr in bash and most other shells.

Having the errors sent to a different output FD is handy.  Cron outputs both stdout and stderr, but part of the Unix philosophy is to say nothing when things go as planned, but complain loudly when things fail.  It is nice to have cron stderr output get forwarded to a human, only if something bad happens and for stdout message to be dumped, as an example.

---

### Post by Alan5127 on 2017-07-24
Hi SeijiSensei,

> **SeijiSensei said:**
> You can stop the errors from appearing on the console by adding
```
2>/dev/null
```
to the end of the command.  The errors are sent to the "syserr" device which is represented by the "2" in the code above.

I tried adding that to the end of the command, but I still get the error lines.

The command now reads as follows - is this correct?:

```
find . -type f -print0 | xargs -0 mediainfo | grep -e "Complete name" -e "Width" > 0000.txt 2>/dev/null
```


> I think the error comes from this part of the command
```
grep -e "Complete name" -e "Width"
```
If you're looking for a line with both "Complete name" followed by "Width" later on you can use the regular expression
```
grep -e "Complete name.*Width"
```
or you can use another pipe to grep
```
grep -e "Complete name" | grep -e "Width"
```

I may be misunderstanding, but don't think that will work.  I need to find rows that contain either 'Complete name' OR 'Width', whereas I think your suggestion would be an 'AND', rather than an 'OR'?

As I mentioned in my OP, the output works fine, my only query is why I am getting the error.

Is it possible to re-write the grep part of the command to perform an 'OR' but not get the errors to the screen?

Thanks for your help,

Alan.

---

### Post by Alan5127 on 2017-07-24
Hi btindie,

> **btindie said:**
> The issue with your above script is that it would split the details for each file over two lines.

Yes - that is as intended and the output to the 0000.txt file is exactly what we wanted.

> **btindie said:**
> One way around it is to create a temporary script to process the media info which would also include the filename on the same line, similar to grep output.

getwidth:
```

mediainfo "$1" | grep -E '^(Complete name|Width)[ ]+' | awk -F: '{sub(/^[ ]+/,"",$2);print $2}' | paste -sd:

```

And run as:
```

find . -type f -exec /path/to/getwidth '{}' \; 2>/dev/null

```


I will file this for later use - I am sure it will come in handy!

> **btindie said:**
> The File read error may be because the file isn't understood by mediainfo. So you may want to extend the getwidth script to first test that the file being queried is recognised by mediainfo.


I haven't found any files that mediainfo is unable to 'parse', but is there a way to get the errors pushed into the txt file, along with the actual data?  If so, I could then check exactly where the errors are occuring (on which files)?

Thanks,

Alan.

---

### Post by &amp;KyT$0P# on 2017-07-24
> **Alan5127 said:**
>  is there a way to get the errors pushed into the txt file, along with the actual data?
Which shell are you using?  If [FONT=Courier New]bash[/FONT] or [FONT=Courier New]ksh[/FONT], try replacing
```
> 0000.txt
```
with
```
2>&1 | tee 0000.txt
```

That should send output and errors to both the terminal and the text file.

---

### Post by Alan5127 on 2017-07-24
> **halogen2 said:**
> Which shell are you using?  If [FONT=Courier New]bash[/FONT] or [FONT=Courier New]ksh[/FONT] 

bash

> **halogen2 said:**
> try replacing
```
> 0000.txt
```
with
```
2>&1 | tee 0000.txt
```

That should send output and errors to both the terminal and the text file.

I just tried that, running this complete command on a directory (with just three video files in it, and no sub-directories):

```
find . -type f -print0 | xargs -0 mediainfo | grep -e "Complete name" -e "Width" 2>&1 | tee 0000.txt
```

That output about 50 lines of the error I posted above, followed by the correct output on the screen.

In the text file, it just gave the correct output - no error lines were in the txt file at all.


Thanks,

Alan.

---

### Post by steeldriver on 2017-07-24
The file that's causing the mediainfo read errors is likely the output file 0000.txt itself, which gets created by the shell before the `find` command is run - try

```

find . -type f [COLOR=#0000ff]! -name 0000.txt[/COLOR] -print0 | xargs -0 mediainfo | grep -e 'Complete name' -e 'Width' > 0000.txt

```

(or create the output file somewhere else - such as the parent directory > ../0000.txt for example)

---

### Post by Alan5127 on 2017-07-24
Hi SteelDriver,

> **steeldriver said:**
> The file that's causing the mediainfo read errors is likely the output file 0000.txt itself, which gets created by the shell before the `find` command is run - try

```

find . -type f [COLOR=#0000ff]! -name 0000.txt[/COLOR] -print0 | xargs -0 mediainfo | grep -e 'Complete name' -e 'Width' > 0000.txt

```

(or create the output file somewhere else - such as the parent directory > ../0000.txt for example)


Brilliant - That was exactly the issue!

I chose to use this (easier for me to understand and see what is going on, but you solved it):

```
find . -type f -print0 | xargs -0 mediainfo | grep -e "Complete name" -e "Width" > ../0000.txt
```

Thank you for solving the mystery.

Alan.

---

