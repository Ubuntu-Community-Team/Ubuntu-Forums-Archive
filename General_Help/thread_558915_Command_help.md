---
title: "Command help"
date: 2007-09-24
forum: General Help
---

### Post by spetroff on 2007-09-24
Hello,

I can use 

grep -ri 'abc*' ./some_dir

to generate a list of lines containing the regexp above, but how can I transform this list into a list of distinct words matching the regexp? That is, grep gives me lines, but I need to generate a list of words containing a regexp. 

As a side issue, the files I am searching are source code, so I also need to consider 'words' not delimited by whitespace. E.g.  if(abc_1==2) might be a matching line, and I need to extract the word abc_1 from it even though the tokens '(' and '=' surround the matching portion. (If this is a PITA, then I can ignore it for now and only consider matches surrounded by whitespace)

Thanks
Shane

---

### Post by energiya on 2007-09-24
a nasty hack that just came in my mind would be
```

grep -ri 'abc*' ./some_dir | sed -e 's/[()=,;{}&:@?]/ /g;s/ /\n/g' | grep abc | sed -e :a -e '$!N;s/\n/ /;ta'

```
This gives you a word list containing abc
It can be improved, and there might be better ways to do this. Post if it doesn't work

Tried with
> 
if(abc_1==2&&abc2==3)
       {abc2=2;abc3=3}

and it returns
> abc_1 abc2 abc2 abc3

---

### Post by spetroff on 2007-09-24
Thanks heaps, that gets me a lot closer!

Let's see if I can parse this to figure out what it means:

sed -e 's/[()=,;{}]/ /g;s/ /\n/g'

Substitute 'source code chars' with blanks (I had to add " to the list to account for string literals, and . for method access, but no biggie)
Substitute blanks with newLines globaly (I didn't realize you could string together sed commands with a semi-colon)
results in lines again, this time one line per word (great idea!)

grep abc 

gives me the stuff I'm interested in again

sed -e '$!N;s/\n/ /g'

Ugh this I don't get. $ = end line, !N = Not something :(   (Any hints?)
Then finally substitute newline with blank again globally

One last requirement (if it's easy) how can I compress this resulting list into a set of distinct values?

Thanks again.

Shane

---

### Post by spetroff on 2007-09-25
just discovered uniq -i It does the trick nicely. 

Still haven't figured out your last sed command though; I can't even figure out why it's needed. If you've got one word per line, you're pretty much done. The process seems to be done after the second grep, just sort it and send it to uniq, et voila!

Thanks again
Shane

---

### Post by energiya on 2007-09-25
> **spetroff said:**
> 
Still haven't figured out your last sed command though; I can't even figure out why it's needed. If you've got one word per line, you're pretty much done. The process seems to be done after the second grep, just sort it and send it to uniq, et voila!
Shane

I thought you needed all the words on the same line. The last sed replaces \n with space, so you don't end up with a column, but I see you don't need that.

BTW, some nice tricks you might use: [http://www.student.northpark.edu/pemente/sed/sed1line.txt](http://www.student.northpark.edu/pemente/sed/sed1line.txt) Very, very usefull.

---

