---
title: "[SOLVED] Batch Renaming of Files"
date: 2008-06-28
forum: General Help
---

### Post by DarkWinterNights on 2008-06-28
Hello all,

I recently just finished tagging a significant number of photos only to discover that my camera had dated them incorrectly.

As an example:
20040613 - Doug Skiing BC.jpg

Rather than manually going through and redating all the files, I was hoping someone might be able to point me in the direction of a utility that can rename part of a file, or better yet, educate me if such a tool is already at my disposal.

Thanks all in advance. :)

E:  Just to clarify, I'm hoping for a utility that would replace a segment of the filename.

---

### Post by dominiquec on 2008-06-28
On the command line, there's a program called "rename".  You'll need to study it a bit, though, because it used regular expressions -- not the most intuitive until you get the hang of it.

There's also a package called gprename and on Xubuntu, there's a bulk renamer that's included with thunar.  You can install thunar package.  Not much experience with either, though, as I use the command line for these things.

---

### Post by neoAnderson on 2008-06-28
I don't know how much experience you have with programming, but if I were you I would write a Perl or Shell script to read all the files from a directory and change their names (based on a convention or a general rule). You can do this by calling the "mv" command from within the scripts, and you can also analyze the names of the files and decide upon a relationship between the older and newer files.

---

### Post by saidinesh5 on 2008-06-28
simply goto add/remove applications in the main menu... and search for "rename"...there are plenty of applications for u ...simply installanyone of them..never really tried them..so cant suggest you much about them..but all of them seem to be approp. for your question..

hope your problem is solved
all d best

---

### Post by ghostdog74 on 2008-06-28
> **DarkWinterNights said:**
> Hello all,

I recently just finished tagging a significant number of photos only to discover that my camera had dated them incorrectly.

As an example:
20040613 - Doug Skiing BC.jpg

Rather than manually going through and redating all the files, I was hoping someone might be able to point me in the direction of a utility that can rename part of a file, or better yet, educate me if such a tool is already at my disposal.

Thanks all in advance. :)

E:  Just to clarify, I'm hoping for a utility that would replace a segment of the filename.
what is the correct format? show an example
```

for files in *.jpg
do
 # get first part which is your date
 # rearrange them
 # mv $files to new file
done

```

---

### Post by DarkWinterNights on 2008-06-28
Wow, I really dropped the ball on that one.

So used to using Windows and having to actually find my software.  lol

Thanks for the help guys.  That solved my issue.

---

