---
title: "Sed"
date: 2020-05-31
forum: General Help
---

### Post by yegnal on 2020-05-31
I am trying to get sed to replace the first two out of three occurrences of a string in a file.

**The three instances are each on their own line, so I need something that will go through and stop after changing only the first two instances.**

I have tried sed "0,/STRIN1/{STRING2//}" ~/.SOMEFILE  ------> does nothing

every other attempt changes all three occurrences which is not what I'm looking to do...


Any hints ?

---

### Post by Holger_Gehrke on 2020-05-31
You could do```

sed '0,/STRING1/s/STRING1/STRING2/' filename

```
This will substitute STRING2 for STRING1 (that's what the 's' stands for) in the lines starting at line 1 (the 0 in the address part means that a match on the first line will end the address range, with a '1' instead it would replace two occurrences if (and only if) one is on the first line) and ending at the first occurrence of STRING1. To replace the first two occurrences you will have to run this twice. 

Holger

Edit: you might want to use the option '-i' because without that sed will send the edited text to standard output. With '-i' or '--in-place' the edited text is written to the file. Or you could do
```

sed '0,/STRING1/s/STRING1/STRING2/' filename|sed '0,/STRING1/s/STRING1/STRING2/'>newfilename
```

---

### Post by TheFu on 2020-05-31
i wouldn't use sed for this.  I&#8217;d use perl or ruby or python where the language provides an easy way to count.  Think it would be 3-5 lines in perl.

---

### Post by yegnal on 2020-05-31
I think my issue is complicated by the intention and the situation.

I have a file with three lines
startingChars followed by lots of other text
startingChars followed by lots of other text
startingChars followed by lots of other text

I'm looking to search for the startingChars and replace with the startingChars plus some replacement text between the 'lots of other text'. i.e.
startingChars+littleSubstitution followed by the lots of other text
startingChars+littleSubstitution followed by the lots of other text
startingChars followed by lots of other text 

Anything I've tried including the answer provided above, and even trying loops and what not doesn't do what's needed.

I'll either get all three lines changed, the first line only, or the first line gets done multiple times causing:
startingChars+littleSubstitution+littleSubstitution+littleSubstitution followed by the lots of other text

---

### Post by yegnal on 2020-06-01
Finally got it to work, got this from somewhere and solution was to run it twice, second iteration with a slight change

$ sed ':a;N;$!ba;s/TEXT/replaceTEXT/1' file
$ sed ':a;N;$!ba;s/TEXT/replaceTEXT/2' file

Wish I new where all those options come from, can't really figure it out from 'man sed' but it works.  
First pass does the first file occurrence and second pass does the second.

---

### Post by norobro on 2020-06-01
From the sed man page [http://manpages.ubuntu.com/manpages/trusty/man1/sed.1.html]("http://manpages.ubuntu.com/manpages/trusty/man1/sed.1.html#addresses:") under "Addresses":
> Sed  commands  can  be given with no addresses, in which case the command will be executed
       for all input lines; with one address, in which case the command will only be executed for
       input  lines  which  match  that address; or with two addresses, in which case the command
       will be executed for all input lines which match the inclusive  range  of  lines  starting
       from  the  first address and continuing to the second address.
       
An example:```
$ cat sed.in
startingChars followed by lots of other text
startingChars followed by lots of other text
startingChars followed by lots of other text
startingChars followed by lots of other text


$ sed -e " 2,3s/startingChars/startingChars+littleSubstitution/" sed.in
startingChars followed by lots of other text
startingChars+littleSubstitution followed by lots of other text
startingChars+littleSubstitution followed by lots of other text
startingChars followed by lots of other text
```Use '\$' in place of the second number (3) to process lines to the end of the file.

---

