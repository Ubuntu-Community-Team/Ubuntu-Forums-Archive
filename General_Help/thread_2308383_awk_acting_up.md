---
title: "awk acting up?"
date: 2016-01-02
forum: General Help
---

### Post by Langstracht on 2016-01-02
I am running 2 machines.

The output of ```
ls -r
```

is > -rw-r--r--  1 allan allan      132 2015-01-30 08:01 work10.sh on the first

and > -rw-r--r--  1 allan allan      136 2015-02-01 08:00 work31.sh (i.e. identical) on the second.

However, when I run 

```
ls -Rl | awk '/^-/ && $1=$1' OFS="," > ~/Desktop/file.csv
```

I get csv output of

> -rw-r--r--,1,allan,allan,1143,2012-10-13,04:51,finance.sh on the first 

and the unwanted, unexpected, unhelpful

> -rwxr-xr-x,1,allan,allan,389784,Feb,11,2014,technical.txt 

on the other.

Anyone know what's going on?

TIA

---

### Post by steeldriver on 2016-01-02
What are you complaining about exactly? The time format? That will be determined by ls using locale settings (LC_TIME, LANG) and the age of the file rather than by awk I think

If you want to make it consistent then look at the --full-time or --time=FORMAT options to ls

---

### Post by Langstracht on 2016-01-02
Thanks for your prompt response.  And sorry that my post was, apparently, unclear.

I am complaining that the lines which end up in the csv files differ between the 2 machines.  I export to csv so that I can do some sorting.  Sorting on the date which appears as 

> ,2012-10-13,04:51,0  is good ... and expected.

> ,Feb,11,2014, is not.  The time is unimportant.  Only the date is of interest.  Although I do NOT understand why that is also different.

Since both machines give identical output from the ```
ls -l
``` command, I have no idea what you are suggesting I do with a further [option] to that command.

---

### Post by steeldriver on 2016-01-02
You showed that ls -l gave the same output (date/time format) **on files less than one year old**: by default, ls treats older files differently:

```

By default, file timestamps are listed in abbreviated form, using a
date like `Mar 30  2002' for non-recent timestamps, and a
date-without-year and time like `Mar 30 23:45' for recent timestamps.
[B]This format can change depending on the current locale as detailed
below.[/B]

```

To stop this happening, you can try telling ls to use a specific format using its --time-style option e.g.

```

ls -l --time-style='+%F %T'

```

Have you considered using 'find' instead of 'ls' + 'awk'? it might be more unambiguous e.g.

```

find -type f -printf '%M,%u,%g,%s,%TF,%TT,%f\n'

```

---

### Post by Langstracht on 2016-01-02
I was not aware of this (I think very odd) date treatment and picked 4 lines at random to "show the problem".  Or so I thought.

In any event I have a problem ... but that ain't it.

On the problematic machine I created a folder and a new file in it and I pasted in the oldest file I could conveniently find.

ls -l on that folder gives

> -rw-r--r-- 1 allan allan      0 2016-01-02 16:37 longwave.mdb
-rwxr-xr-x 1 allan allan 135168 1997-12-20 15:00 shortwave.mdb 

```
ls -Rl | awk '/^-/ && $1=$1' OFS="," > file.csv
```

in the folder gives this:

> -rw-r--r--,1,allan,allan,0,2016-01-02,16:37,longwave.mdb
-rwxr-xr-x,1,allan,allan,135168,1997-12-20,15:00,shortwave.mdb in the csv file.

And, consequently, this:

> -rw-r--r--	1	allan	allan	0	2016-01-02	16:37	longwave.mdb
-rwxr-xr-x	1	allan	allan	135168	1997-12-20	15:00	shortwave.mdb
 in the .ods file.

So ... I have absolutely no idea what gives.  Perhaps after so many lines it goes squirrely 

I'll see how I get on with "find" ... but that's for tomorrow.

---

### Post by vasa1 on 2016-01-02
> **steeldriver said:**
> ...: by default, ls treats older files differently:
...
Have you considered using 'find' instead of 'ls' + 'awk'? it might be more unambiguous e.g.
...
This fits in well with what I've read elsewhere and experienced. There may be better tools...
For example:
[https://github.com/koalaman/shellcheck/wiki/SC2012](https://github.com/koalaman/shellcheck/wiki/SC2012) and a quote from there: *ls is only intended for human consumption: it has a loose, non-standard format and may "clean up" filenames to make output easier to read.*
[http://askubuntu.com/questions/272623/can-ls-l-be-made-to-separate-fields-with-tabs-rather-than-spaces-to-make-the-ou](http://askubuntu.com/questions/272623/can-ls-l-be-made-to-separate-fields-with-tabs-rather-than-spaces-to-make-the-ou)
and
[http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

---

### Post by Langstracht on 2016-01-03
I've now tried "find" ... and, in terms of format and "column content" it works just fine.  Thanks for that.

But, and it's a big but, in contrast to "ls", find also returns the gazillion files in hidden folders.  And, if there is a way to get the command to ignore hidden folders, I can't find it.

Is there a way?

---

### Post by steeldriver on 2016-01-03
You should be able to use find's '-path' and '-prune' to exclude hidden files/dirs (i.e. anything with a dot right after a /) similar to ls -lR:

```

find . -path '*/\.*' -prune -o -type f -printf '%M,%u,%g,%s,%TF,%TT,%f\n'

```

If you'd like to take a step back and tell us your end goal is someone might be able to suggest a better method

---

### Post by Langstracht on 2016-01-03
I thought I had indicated I wanted to get file information output into a spreadsheet so that I can do some sorting and analysing.

That said the latest command works just fine.  And thank you for that.

Of course if someone else has an alternative ...

---

