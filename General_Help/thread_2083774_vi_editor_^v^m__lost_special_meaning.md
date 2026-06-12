---
title: "vi editor ^v^m  lost special meaning"
date: 2012-11-13
forum: General Help
---

### Post by uuuuserrrr on 2012-11-13
I am looking for something that doesnt lose its special function when writing a script. I am trying to use vi editor to change many files and cannot find any solution.

:g/G53G28G49Z-\.25/s//G90G53G49Z0%0d G91G28Z0/g
                                         or
:g/G53G28G49Z-\.25/s//G90G53G49Z0^v^m G91G28Z0/g

I have tried these without success, as you can see I am trying to get a ctrl-v ctrl-m . these both work when typed into vi , but when passed from elsewhere or even cut and pasted it loses its original function.

any ideas, or another solution ?

---

### Post by Cheesemill on 2012-11-13
What exactly are you trying to achieve by using vi?

You can use the sed or awk commands to achieve everything that I can think of that you would use vi for.

---

### Post by uuuuserrrr on 2012-11-13
I am just more familiar with vi. I was assuming that I may have the same issue with those tho. what would the command for those look like?

---

### Post by Cheesemill on 2012-11-13
> **uuuuserrrr said:**
> I am just more familiar with vi. I was assuming that I may have the same issue with those tho. what would the command for those look like?
Again, that depends.

What exactly are you trying to achieve using vi?

---

### Post by uuuuserrrr on 2012-11-13
I am trying to replace a string of characters with another string of characters and another line of characters on about 500 files.

---

### Post by Cheesemill on 2012-11-13
Vi isn't meant to be used in scripts, only interactively. The preferred method in this situation would be to use sed.

To do a find and replace with sed you would use:
```
sed -i 's/searchterm/replacement/g' filename.txt
```This will replace all occurrences of searchterm with replacement in the file filename.txt

You can add the find command to do this over multiple files at the same time, for example to do a find and replace in every file in a directory you could do:
```
find /home/user/directory -type f -exec sed -i 's/searchterm/replacement/g' {} \;
```

---

### Post by smss on 2012-11-13
Are you wanna to find a string? I known your mean as well?
Try with this command in terminal : ```
 grep -i "string" files.* 
```

---

### Post by uuuuserrrr on 2012-11-13
thanks
i will try tomorrow, maybe the ctrl functions wont be lost there

---

### Post by steeldriver on 2012-11-13
If you're trying to replace DOS-style line terminations then in 'sed' it's probably less ambiguous to use the escape character \r rather than using the Ctrl-v Ctrl-m control sequence (since ^M could be read as an anchored literal M)

```
$ sed -i 's/\r$//'
```

---

### Post by uuuuserrrr on 2012-11-13
i cannot try that right now, as i am not near a computer now, but i will try further to clairify what i am trying to do.

i need to replace a string and add a additional line after.

example
original: fo fo fo [search string]

desired: fo fo fo [replace string]
[additional line of replace string]

my issue is that the ^v^m is coming over literaly when using it,  other than in the command line

---

### Post by JKyleOKC on 2012-11-13
> **uuuuserrrr said:**
> my issue is that the ^v^m is coming over literaly when using it,  other than in the command lineThat's because the Ctrl-v escape sequence is part of bash, the shell processor, not part of vi or vim.

To do what you want, use the \n newline escape. The end-of-line indicator in all *ix files is 0x0a, not 0x0d, so even if what you tried worked, it would not do what you expected it to do. Microsoft uses the CR-LF convention, but everything descended from Unix uses simply LF.

---

### Post by uuuuserrrr on 2012-11-13
thanks, i think thats what i needed. i will try in the morning.

---

### Post by uuuuserrrr on 2012-11-14
I am not having any success. I guess I need to read the man pages for sed and awk. seems to be a few threads on other sites refering to using sed for this and having issues too.

---

### Post by Cheesemill on 2012-11-14
If you post the actual commands you are trying and the file(s) you are trying them on then maybe we can help.

---

### Post by uuuuserrrr on 2012-11-14
:g/[search string]/s//[replace string ^v^m additional line]/g
this works fine in vi , which is actually using ex or ed , i am not sure.

I can process this and just come back with sed or something and change the new line character to a actual new line. I just need something that will do this.

thanks for all the help ,but i need to work on some other stuff for a day or two before I can get back to this.

---

### Post by steeldriver on 2012-11-14
in sed, the easiest way would probably be something like 

```
sed -i 's/search string/replace string[COLOR=Red]**\n**[/COLOR]additional line/'
```[you could use the sed 'a' ('append') command for the additional line, but it's not necessary if the additional line exactly follows on from the replacement string]

---

### Post by Cheesemill on 2012-11-14
As mentioned earlier you need to use \n for a new line instead of ^v^m.

---

### Post by kjohri on 2012-11-14
Try this,

:1,$s/old-string/new-string/g

That is, 

:1,$s/G53G28G49Z-\.25/G90G53G49Z0%0d G91G28Z0/g

1,$ means the entire file (first and the last lines). To work on a part of the file, you can replace 1,$ by the relevant line numbers.

The following link gives more details,

[http://www.softprayog.in/tutorials/vi-editor-commands]("http://www.softprayog.in/tutorials/vi-editor-commands")

---

### Post by uuuuserrrr on 2012-11-15
am not having any luck
i am also using irix 6.5.2 where sed does not have the -i option, so i need a work around there too.

the \n or \r\n or ^v^m or \  are all being output literally.

the exact commands are as suggested, but here they are for examination

sed "s/[search string]/[replace string] \n [additional trailing line]/g" [input file] > [output file]
sed s/[search string]/[replace string]\n[additional trailing line]/g [input file] > [output file]

sed "s/[search string]/[replace string] \r\n [additional trailing line]/g" [input file] > [output file]
sed s/[search string]/[replace string]\r\n[additional trailing line]/g [input file] > [output file]

sed "s/[search string]/[replace string]\a[additional trailing line]/g" [input file] > [output file]
sed s/[search string]/[replace string]\a[additional trailing line]/g [input file] > [output file]

i am not sure if i am using the append option correct here or not

also i have cygwin running on a windows box and checked out the man page for sed there, comparing it to the version i am using on the irix machine and toke note of this note:
------------------------------------------------------------------------------
REGULAR EXPRESSIONS
     POSIX.2 BREs should be supported, but they aren't completely because of
     performance problems.  The \n sequence in a regular expression  matches
     the newline character, and similarly for \a, \t, and other sequences.

------------------------------------------------------------------------------

has anyone actually tried this and had success?
~

---

### Post by steeldriver on 2012-11-15
> **uuuuserrrr said:**
> 
has anyone actually tried this and had success?


The sed syntax we have given you is certainly correct for GNU sed - if IRIX doesn't support it that's a different matter

```
$ cat myfile
line
line
line
line to replace
line
$
$ sed 's/line to replace/replacement line\nadditional line/' myfile
line
line
line
replacement line
additional line
line
$ 

```

EDIT: if platform limitations mean that you must use the 'a' command, then something like this should work:

```
$ sed -e 's/line to replace/replacement line/' -e '/replacement line/ a\
additional line' myfile
```

---

### Post by uuuuserrrr on 2012-11-15
thanks steeldriver
  I found that on cygwin  the \n works , but not the \a
i could maybe use that if i could figure out how to mount my xfs drive to that.
it has been 8 or 10 years since i have had a linux box. this was probably the last straw.

---

### Post by Slim Odds on 2012-11-15
If all that you want to do is convert DOS line endings to Unix, why don't you just use the 'dos2unix' command?

---

