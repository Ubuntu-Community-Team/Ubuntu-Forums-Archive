---
title: "Grep cut or awk?"
date: 2008-06-19
forum: General Help
---

### Post by wortxyzzy on 2008-06-19
ok, so im trying to automate a few Firefox tasks that i would like to continue around the clock.    If i were on a windows box i would just macro express it but in Linux it seems a little more tricky but also maybe a little more fun.

I have an updating file with numbers in them like these:
=54333
=54055
=54067
=54107
=54467
=54466
=54246
=54105
=54056
=54029
=54286
=54288

This list updates, it is a plain text file.
How can i from the terminal select each individual line and drop it in as part of a 
$firefox [http://some](http://some) web site/the number


This could be with a script or anything i can call from the terminal. I've been reading mad man pages and can't seem to find just what i need. Or if i have it was a little beyond my understanding.

---

### Post by mike2357 on 2008-06-19
Will this do what you want (assuming your file with the data is called my_file) ?

cat my_file | awk ' {print "$firefox http://www.some_web_site.com:" $0}'

In the above example, $0 means print the whole line from my_file.  When I want to use awk, I often end up doing a using my favorite search engine to look for a go-by.

---

### Post by wortxyzzy on 2008-06-19
This is very nearly exactly what I need.  
With your example the proper web addresses print to the terminal perfectly.
But what I'm actually needing is for them to be terminal commands with a given delay in between each one.

I would like my script to open these web pages from the terminal. with the "firefox" command it will open a new tab which is perfect,

Thanks

---

### Post by wortxyzzy on 2008-06-19
By appending "| bash"    to the end of the 
cat results-file | awk ' {print "firefox website" $0}' 
i have it send them to the terminal, but how would i say get 1 minute between each one being sent?

---

### Post by geirha on 2008-06-19
Here's one using only bash
[php]
for number in $(<results-file); do
  firefox "http://something/$number"
  sleep 60     # sleep for 60 seconds
done
[/php]

---

### Post by Catalyst2Death on 2008-06-19
could you use a sleep command somehow?

```
$ sleep 1 && cat results-file | awk ' {print "firefox website" $0}' | bash
```

this would allow you to send it to bash, and the next time it was run, then you would have a one second pause before executing the line.

---

### Post by wortxyzzy on 2008-06-19
thanks for all the help,
Im sure there are actually hundreds of solutions. what i wound up doing was

cat results-file | awk ' {print "sleep 180 && firefox http://site/" $0}' | bash

works like a charm

---

