---
title: "Sed Question:  How to insert space in a pattern match"
date: 2019-07-24
forum: General Help
---

### Post by frrobert on 2019-07-24
I am converting some vimwiki files to markup format.

One of the issues I am having a few of the heading are missing spaces.

The vim wiki headings should be = Heading = with a space before and after the word or words used for the heading.  Headings will have 1 to 3 = on each side depending on the level of the heading.

A few of the tags are misformed for example =Heading = or =Heading= or = Heading=

I need to adjust the headings so they are = Heading = I was able to find the match but I can't get the replace to work right.  Anything I come up with put the space before or after the two letter pattern.  

I am fairly new to sed so any help would be appreciated.

Thanks

---

### Post by &amp;KyT$0P# on 2019-07-24
Could you please post the exact sed command you're trying?

---

### Post by dragonfly41 on 2019-07-24
You can install [pandoc]("https://pandoc.org/MANUAL.html") and try conversion

vimwiki to markdown

---

### Post by SeijiSensei on 2019-07-24
Are you enclosing the string inside single quotes? 

```
sed 's/=+.*Heading/= Heading/g' | sed 's/Heading.*=+/Heading =/g' < file > newfile
```

That should match a string with one or more equal signs followed by one or more characters then Heading and replace it with "= Heading", then do the same for the other end. Warning this is completely untested.

You need the single quotes so that bash won't interpret embedded spaces as a delimiter.

---

### Post by frrobert on 2019-07-25
Thanks everyone for their help.
Dragonfly: I am actually trying to convert Vimwiki to md but Pandoc will only convert the header correctly if there is a space between the header and the equal signs framing it.
SeijiSensei:  No Joy.
halogen2:  here is the command I was trying.  Please note this sends it to std out so I could see if it did what I wanted before actually changing any file.
sed 's/=[a-zA-Z]/& /g' 2019-07-23.wiki  
It puts the space in the wrong place.
At this point it has just become a thought experiment, I don't need the answer but it still would be cool to know how to make it work.  I ran grep to see how many files there were to be changed and the number was doable by hand, not enjoyable but doable.  So I manually made the changes early today.  So now I can do the conversion to markdown using Pandoc.

Thanks again.

---

### Post by norobro on 2019-07-25
If I understand your problem the following using extended regexes (-E or -r) seems to work:```
sed -r  's/=\s?Heading\s?=/= Heading =/g'
``````
$ printf "=Heading=\n= Heading=\n=Heading =\n" | sed -r 's/=\s?Heading\s?=/= Heading =/g'
= Heading =
= Heading =
= Heading =

```

---

### Post by dragonfly41 on 2019-07-25
Another useful tool (GUI) which uses regex is SearchMonkey (in Ubuntu repo).  I use this quite often to search through files for patterns.

---

### Post by frrobert on 2019-07-27
Thank you everyone for their help.  norobro your code worked.

---

