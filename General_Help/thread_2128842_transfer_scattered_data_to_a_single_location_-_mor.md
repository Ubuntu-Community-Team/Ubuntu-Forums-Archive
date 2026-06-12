---
title: "transfer scattered data to a single location - more errors than success"
date: 2013-03-24
forum: General Help
---

### Post by twinturbotom on 2013-03-24
Data from multiple sources is scattered across a drive.  I would like to find similar files (say all my finance and tax info) and move it to a single location.
I appreciate any direction you can offer; I've been using linux actively for a month or two and am proud of how close I've come to a solution so far!

Where I am now:[INDENT]Find all files and output to a file:
```
find /media/time_capsule/* >> ~/Documents/find_time_capsule 
```

copy grep found files from find output file:
```
cat find_time_capsule | grep 'taxes\|finan' | xargs cp -t ~/Documents/finance/
```
I also tried using -exec instead of xargs...errors for that as well...
[/INDENT]

Problem (long reoccuring set of similar problems):[INDENT]```
xargs: unmatched single quote; by default quotes are special to xargs unless you use the -0 option
cp: omitting directory `/media/time_capsule/Vault/Personal/Personal/2008'
cp: cannot stat `taxes': No such file or directory
```
[/INDENT]

I tried xargs -0 options but that also created one large output error.

I feel like this may be due to carriage returns in my input file, spaces in directories or names, grep output, or something I just can't grasp.  Any thoughts?  I appreciate the mind share...

Background:

My stategy (please off different logic)
[LIST=1]
[*]create a file listing file locatisons & name 
[*]search the file 
[*]copy each file found to a single location 
[*]remove original files 
[/LIST]

I know I can combine this into a single line but I do want to break up certain aspects of the procedure.  

[LIST]
[*]For example 1-4 could be something like:  find *name | grep tax | mv destination
[LIST]
[*]I don't want to combine cp and rm with mv because I may want originals intact
[*]I'd like to output a file of directory contents so I don't have to keep running find for each new term I may add at a later date
[/LIST]
[/LIST]

UPDATE:
copied files with something like this:

for i in `cat find_time_capsle | grep 'tax\|finan' `; do cp $i finance; done
Copied many files and spit out many errors (FILE = name of file):
cp: failed to get attributes of `FILE': No such file or directory
cp: cannot stat `FILE': No such file or directory

---

### Post by steeldriver on 2013-03-24
The safest way to handle filenames that may have spaces or other awkward characters is to tell 'find' to separate the results with a null character

```
find media/time_capsule -type f -print0 > find_time_capsule
```

Note that you don't need a wildcard on the path - but you probably do want to specify '-type f' so you get just the plain files (not dirs)

You can then read the list back in with a 'read' loop

```

while read -r -d $'\0' file
do
  *something to "$file"*
done < find_time_capsule

```

where *something* is cp, mv, grep or whatever

---

### Post by twinturbotom on 2013-03-24
I appreciate the reply...  I wasn't able to get it to work.

```
  find -type f -print0
```
created a binary file, I would like to be able to read it.

The loop didn't quite work for me... most likely because of what I put in the loop!  

while read -r -d $'\0' find_time_capsule
do grep 'tax\|financ' | -xargs cp -t ~/Documents/finance/
 done < find2_time_capsule

Errors:                                                                                                   
cp: cannot stat `Binary': No such file or directory
cp: cannot stat `file': No such file or directory
cp: cannot stat `(standard': No such file or directory
cp: cannot stat `input)': No such file or directory
cp: cannot stat `matches': No such file or directory

I played around with my input file and file name in the loop... either returned errors or hung up my machine..

the 
```
read -r -d $'\0'
```

is completly new to me, 'man read' doesn't show -r or -d so I don't know what is happening with that line, could you elaborate?

I did get something to work for some of the files... I'll update my original post with what I have so far.

Thanks again, enlightening!

---

### Post by steeldriver on 2013-03-24
AFAIK 'print0' doesn't create a binary file - it just uses the  null character instead of a newline as a separator - if you really need  the file to be newline separated for human readability that's fine, just replace the 'print0'  with a plain 'print' and delete the corresponding -d $'\0' from the read command

```

find media/time_capsule -type f -print > find_time_capsule

```

Also if you're using a 'read loop' you don't need xargs because the filenames are processed one at a time

```

while read -r filename
do 
   # echo the filename through grep, and test if the result is a non-empty string
   if [ -n "$(echo "$filename" | grep 'tax\|financ')" ]; then
     echo cp -t ~/Documents/finance/ "$filename"
   fi
done < find_time_capsule

```

or using a 'here string' instead of the echo pipe, so we can use the return value of grep directly in the conditional

```

while read -r filename
do 
   # test the return value as boolean and do something if it is true
   if grep -q 'tax\|financ' <<< "$filename" ; then
     echo cp -t ~/Documents/finance/ "$filename"
   fi
done < find_time_capsule

```

or changing the if...then to a conditional evaluation

```

while read -r filename
do 
   # test the return value as boolean and do something if it is true - based on conditional evaluation
   grep -q 'tax\|financ' <<< "$filename" && echo cp -t ~/Documents/finance/ "$filename"
done < find_time_capsule

```

or (using a bash regex to avoid the need for grep)

```

while read -r filename
do 
   [[ "$filename" =~ tax|financ ]] && echo cp -t ~/Documents/finance/ "$filename"
done < find_time_capsule

```

(I've left 'echos' in the cp statements so you can try them without actually doing anything - you also might want to add a -i to the greps to make them case-insensitive)

Just some ideas to play with, I'm sure I've made some 'bash pitfalls' along the way - you could even make it into a little script and pass in a regular expression for the files you want to match / copy and then do 

```

   [[ "$filename" =~ $re ]] && echo cp -t ~/Documents/finance/ "$filename"

```

EDIT: I know you said you didn't want a one-liner, but for the record I'd probably try something like

```
find media/time_capsule -type f \( -iname '*tax*' -o -iname '*financ*' \) -exec echo cp -t ~/Documents/finance {} +
```

Again, no need for xargs with modern versions of 'find' supporting the '{} +' syntax

[http://www.gnu.org/software/findutils/manual/html_mono/find.html#Multiple-Files](http://www.gnu.org/software/findutils/manual/html_mono/find.html#Multiple-Files)

---

### Post by schragge on 2013-03-24
If you don't need to keep the listing of all files then simple find with -exec action should be enough:
```

find /media/time_capsule -type f -iregex '.*\(tax\|financ\).*' -exec mv -vt ~/Documents/finance/ -- {} +

``` [s]Better quote '{}' as find puts filenames as is, and if they contain spaces this will confuse mv/cp.[/s][highlight]Edit.[/highlight] Not needed, thanks **steeldriver**

---

### Post by steeldriver on 2013-03-24
Hmm.. I thought {} was space safe?

```

$ mkdir ~/Documents/finance
$ 
$ find test -type f \( -iname '*tax*' -o -iname '*financ*' \) -exec cp -vt ~/Documents/finance {} +
`test/dir1/[COLOR=#0000ff]**2012 tax return**[/COLOR]' -> `/home/steeldriver/Documents/finance/[COLOR=#0000ff]**2012 tax return**[/COLOR]'
`test/dir2/financials' -> `/home/steeldriver/Documents/finance/financials'
$ 
$ ls ~/Documents/finance/
[COLOR=#0000ff]**2012 tax return**[/COLOR]  financials
```

I know the \( ... -o ... \) is ugly, but I always have trouble with '-iregex' - I seem to recall it tests against the whole pathname not the filename

```

$ find test -type f -iregex 'tax\|financ'
$ 
$ find test -type f -iregex 'financ'
$ 
$ find test -type f -iregex '.*financ.*'
test/dir2/financials
$ 
$ find test -type f -iregex '.*\(tax\|financ\).*'
test/dir1/2012 tax return
test/dir2/financials
```

---

### Post by schragge on 2013-03-24
Yes, you're right on both accounts. I stand corrected. > **steeldriver said:**
> Hmm.. I thought {} was space safe?I can swear I have read this somewhere, but cannot find the source anymore. All I see is mention of quoting {} from shell in *man find*, but [it's no longer needed]("http://unix.stackexchange.com/questions/8647/gnu-find-and-masking-the-for-some-shells-which") in modern shells. [highlight]Update.[/highlight] [Found](http://www.softpanorama.org/Tools/Find/using_exec_option_and_xargs_in_find.shtml) it. Obviously, softpanorama got it wrong. 

> I seem to recall it tests against the whole pathname not the filename :oops: You are right again. I've changed my post.

---

### Post by steeldriver on 2013-03-24
^^^ I'm sure I've posted the same thing in the past, I'm still not sure whether it's always safe (your link mentions subshells?)

FWIW the above iregex will match anywhere in the path - that may be what the OP wants i.e. find files whose name **or** location includes the match terms

```

$ find test -type f -iregex '.*\(tax\|financ\).*'
test/dir1/[COLOR=#0000ff]**taxdir**[/COLOR]/somefile
test/dir1/2012 [COLOR=#0000ff]**tax**[/COLOR] return
test/dir2/[COLOR=#0000ff]**financials**[/COLOR]
```

I'm not sure the best way to make it match only at the end (i.e. the filename portion) - maybe

```

$ find test -type f -iregex '.*\(tax\|financ\)[COLOR=#0000ff]**[^/]*$**[/COLOR]'
test/dir1/2012 tax return
test/dir2/financials
```

---

### Post by twinturbotom on 2013-03-25
This discussion is GREAT.  Thank you for the multitde of options and examples to learn from.  I'm unfortunatly a bit tied up today and won't be able to learn / try each of the suggestions.  Hopefully over the next day or two I will.

Thank you all for your efforts; it is much appreciated!

a few notes... I do want to grab directoires and files.  If a "taxes" folder exists and had files "2008,2009,...etc." I'd want all that.
important for copy input to come from a file listing (a master find output).  I hate running find multiple times!

Thanks again, very helpful stuff!

---

### Post by twinturbotom on 2013-04-02
I've been able to learn and apply alot from everyones contributions.  Thank you.
In the end I found a bunch of files with odd names containing ('&',';') which caused issues when passing those strings to be copied.  After fixing that I used the following to read my file listing file, pass it to cp:

```
cat $WD_WF | xargs -I {} cp --parents -u {} $WD
```

$WD_WF and $WD are my working directories working file and my workign directory.

Thanks for the help!

---

