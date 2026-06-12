---
title: "bash scripting"
date: 2013-03-11
forum: General Help
---

### Post by then_dude on 2013-03-11
hello,

   i'm always trying to do as most as possible via bash scripting, although i have to ask a  lot of help here on the forum; (great thank you)   

well i have a bash script for printing pdf's in a directory (2 pages per sheet, duplex, fit to page)  

#!/bin/bash  
for file in *.pdf do   lp -o media=a4 -o number-up=2 -o fit-to-page  -o sides=two-sided-long-edge "$file" done

   i got 2 questions:   

1)how can i modify the script to print everything in a directory (say: work)  (included all pdf's in directories under the directory work: for example /work/monday/ ) is it possible to first search all pdf files with the find command and then feed them into de existing script ? that way i could automate a lot of scripts  

2)is it possible to print to a new pdf file; something like an automated pdftk; i suppose again with the find command coupled with the pdftk i could get there.

   thanks guys and ladies

---

### Post by steeldriver on 2013-03-11
There are several ways to "do something" with a bunch of files from a 'find' command, including just piping and piping via xargs. However a nice robust way that I've picked up from one of the smart folks on here is

```

while read -r -d $'\0' file
do
  something with "$file"
done < <(find */path/to/search* *tests* -print0)

```

What I like about it is (a) it handles any legal filename without word-splitting and (b) [I think - never really tested it] it buffers the 'find' output in a similar way to xargs - which just piping the find output to the "do something" command may not

---

### Post by then_dude on 2013-03-11
thanks steeldriver,

but i don't get it, 
i have read the manpage of the read command. 
could you please elaborate a bit ? or use it with my script ? 

sorry, but this is to hard for me.

---

### Post by Vaphell on 2013-03-11
```
while read -r **-d $'\0'** file
do
  echo "working with file $file"
   lp -o media=a4 -o number-up=2 -o fit-to-page -o sides=two-sided-long-edge "$file"
done < <(find /path/to/stuff -iname '*.pdf' **-print0**)
```

it does pretty much the same thing as *for file in *; do ... done* but in a more roundabout, recursive way.

*find* looks for files according to criteria you give it (eg -iname '*.pdf') and its null-delimited output (-print0) feeds the loop.
General idea is this:
```
while read variable(s) ; do [stuff with variable(s)]; done < <( some_command )
```
By default *while read* combo will eat 'records' delimited by newlines one by one (in other words line by line), but here we set delimiter to null char to match the format of *find* output ( -d $'\0'). That means that each filename found by *find* gets in perfect condition to the loop body inside the *file* variable and from now on it's exactly the same story as with the *for* loop

and if you want to simply see the file names, just run the same *find* command but without -print0 (it's not too human readable with it)

---

