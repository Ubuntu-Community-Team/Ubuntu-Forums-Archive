---
title: "Mission impossible?"
date: 2024-02-19
forum: General Help
---

### Post by Langstracht on 2024-02-19
I have a bunch of files in a bunch of sub-directories which may or may not contain specific text.

For instance D001, D002, D003 ... may be in the files.

I need to output a list of which TEXT(s) exist.  I don't want to know which file they are in only that they exist.

So I would look for "D0" in the directory and the output would be D001, D002, D003 etc.

I have fiddled around with find and  grep to no avail.

Can anyone help?

Much appreciation in anticipation

---

### Post by The Cog on 2024-02-19
I assume they are all D followed by three digits. If so, maybe this would do the trick?
```
grep -R -o 'D[0-9][0-9][0-9]' | sort -u
```

---

### Post by Langstracht on 2024-02-19
Thanks for your prompt reply.

I guess I misled you.  Sorry.

The sought text could be any length (D0010, D00022, D00045, ...) BUT all starting with D00 ...

So think: 

        look for "star", output start, started, starlight ...

---

### Post by dragonfly41 on 2024-02-19
I suggest   [https://itsfoss.com/ripgrep-all/](https://itsfoss.com/ripgrep-all/)

using wildcards

also a GUI: Recoll  (but RipGrep is easier for me)

---

### Post by MAFoElffen on 2024-02-19
> **The Cog said:**
> I assume they are all D followed by three digits. If so, maybe this would do the trick?
```
grep -R -o 'D[0-9][0-9][0-9]' | sort -u
```
> **Langstracht said:**
> 
The sought text could be any length (D0010, D00022, D00045, ...) BUT all starting with D00 ...

Modified:
```
grep -E 'D00*[0-9][0-9][0-9]' ./* | sort -u
```

Note: Only one of 'very many ways'.

---

### Post by The Cog on 2024-02-20
Both of these would match the given string definition. It's a very flexible definition we've been given.
```
grep -E -r -o 'D00.+' | sort -u
grep -E -r -o 'D00[0-9]+' | sort -u
```

---

### Post by Langstracht on 2024-02-20
Your suggested commands "work" - thank you - but the output is not what I want/need.

As I tried to explain earlier, I need the output to be just the sought after text - D00111 or whatever.  Not the complete line on which it occurs.

---

### Post by The Cog on 2024-02-20
You haven't defined the "sought after text". It seems to start with "D00" but "could be any length". Actually, with your current definition, everything from "D00" to the end of the file is a valid result.

---

### Post by Langstracht on 2024-02-20
I'm afraid I don't really understand the problem that you are having.  

But let me try to do this again.

Any file in a folder may,or may not, contain the words star, startle, started, starlight.

I would like to discover which of these words are in a file  and output them  - the words NOT the line they appear on.

So I would command

     grep -r "star"

and this WILL locate and output the line(s) on which any of these words appear.

So how do I get it to just output the found words?

---

### Post by The Cog on 2024-02-20
Define what constitutes the start and end of the search text. With words, we can perhaps assume that a non-alpha character (space, comma etc) marks the end of the word. With egrep, we could search for '\bstar\w*\b' except that grep thinks that \w (meaning letters in a word) includes underscore, so that stars_and_stripes would be seen as one word. That may or may not matter to you. Would "superstar" be a match for you?

But you have described wanting to search for "D00" followed by an indeterminate length something. Where does it start or end? Messing around, I found a file here that contains "MAP_RESERVED0080". Does that match? What about "D0080x994-w pop"? 

This will find all strings starting with D00 followed by any numbers of digits. If it sees "MAP_RESERVED0080xyz" it will output "D0080". 
```
grep -r -E -o -h 'D00[0-9]+' | sort -u
```

---

### Post by Langstracht on 2024-02-20
Perfect!!!

The output is EXACTLY what I was looking for.

Thank you SO MUCH!

---

### Post by TheFu on 2024-02-20
Another Homework problem SOLVED!

---

### Post by The Cog on 2024-02-20
For some reason, that hadn't crossed my mind. Maybe it is.

---

### Post by TheFu on 2024-02-20
> **The Cog said:**
> For some reason, that hadn't crossed my mind. Maybe it is.

Hard to tell.  The problem did seem a little advanced for a typical class, but who knows?  Also, people with 18 yr old accounts usually don't have homework. ;)

Regex is hard for people to learn and there are a bunch of different regex engines, each is slightly different.  I happen to know regex pretty well due to a job I had for 3 yrs where it was used to create hyperlinks inside PDF files - table of contents, Table of Figures, Table of Tables, and Indexes withing thousands of documents.  We standardized on the perl regex engine since it includes all the features.  Ruby and egrep generally do as well.  Regular "grep" and "sed" don't and I struggle with those, since they lack some features I depend on.

There are regex trial engines on the internet.  Sadly, they aren't all meeting the same regex engine standards - especially those based on the Javascript language, so I find them of almost zero use for my needs, but they do exist for simple questions line this thread.

Also, an AI tool shown in put lines and expected output lines would easily create a working regex if the tools to be used were specified.

Actually, this thread would have been easier to understand if  a few "input lines" and "needed output lines" would have been provided.  Asking easy to understand, complete, questions is hard sometimes.  The OP has to realize, we only know what is provided here unless the inputs and outputs are in a well-known standard format.

---

### Post by dragonfly41 on 2024-02-21
In this forum we humans can scratch our heads to work out what is asked in a post.
But when we pose questions to AI assistants it seems we now have to learn the new art of "prompt engineering".

[https://www.ibm.com/topics/prompt-engineering](https://www.ibm.com/topics/prompt-engineering)

---

