---
title: "how to scan and remove duplicates from many text files in a folder?"
date: 2016-08-25
forum: General Help
---

### Post by hopelessone on 2016-08-25
Hi,

I have 1/2TB of text files in a folder.

I want to keep the text file names.

How can i go through a file and compare each line to all the rest, removing dups, then start next file.. etc until all done?

Any ideas would be very helpful :)

---

### Post by sudodus on 2016-08-25
Do you want to compare a whole file with another whole file (with another name), and remove duplicate files?

Or do you want to compare a line in a file with the other lines (in the same file), and remove duplicate lines (and do the same for all the files)?

It makes it easier to help, if you describe with more details what you want to do. Please show a real example.

---

### Post by hopelessone on 2016-08-25
ahh, yep sorry, want to remove all instances of a single word in all files in that folder.

eg.
textfile1.txt has dupe word ***power***
textfile2.txt also has this word ***power ***and needs to be removed etc...

so use the first file to check against the other files, once finished checking and remove all dupes, then begin second file and do same until all done..

---

### Post by sudodus on 2016-08-25
It is still not clear (for me).

- Do the files contain more than one word each?

. In that case, is the order of lines and words important, or can the lines or words be sorted in alphabetical order?

. Do you want to remove duplicate words from each file (remove all duplicates also within a file), or do you want to remove an entire file, that contains a duplicate word?

---

### Post by steeldriver on 2016-08-25
And what is the format of the files? are they simple wordlists, or free-form text?

What is your end goal i.e. what are you going to do with the files after? why do they need to be de-duped in this way?

---

### Post by hopelessone on 2016-08-25
Some of the files are 100Gb, 1,000s of words each file, they are all text files, format is simple wordlists, 1 word per line, order is irrelevant, each file does not have duplicates.

I want to remove duplicate words from each file in the entire dir. End goal is to reduce the overhead when using hashcat, they need to be de-duped to reduce overall time running 500GB of files through hashcat. file extensions are .txt .dic .lst

---

### Post by hopelessone on 2016-08-25
I have 4Gb memory, 1TB spare space. Hope that helps :)

---

### Post by sudodus on 2016-08-26
I'm thinking of a shellscript or compiled program, that does the following. A shellscript might be easier to create, but a compiled program might work faster. I may have overlooked or misunderstood something, but it could be a help for you to get started:

I'm assuming that you have files with one word per line and no trailing spaces or other 'cruft' that would confuse the process.

Maybe the easiest option would be to start with a master file, for example the biggest one. Sort the lines alphabetically with ***sort*** and remove duplicates (within the file) with ***uniq***.

The next step is to store unique words from the other files.

Read each line of the second file, check it versus the master file, and write unique lines to a subdirectory (a file with the same name in the subdirectory). That way you get a file with unique words from the second file.

Read each line of the third file, check it versus the master file and the copy in the subdirectory of the second file, and write unique lines to the subdirectory (a file with the same name in the subdirectory). That way you get a file with unique words from the third file.

...

Read each line of the last file, check it versus the master file and the copies in the subdirectory of the previous files, and write unique lines to the subdirectory (a file with the same name in the subdirectory). That way you get a file with unique words from the last file.

Then, if you wish, you can copy or move the master file to the subdirectory, and you should have a set of files with unique words in the subdirectory.

---

### Post by HermanAB on 2016-08-26
fslint

[http://www.howtogeek.com/201140/how-to-find-and-remove-duplicate-files-on-linux/](http://www.howtogeek.com/201140/how-to-find-and-remove-duplicate-files-on-linux/)

---

### Post by kloszard on 2016-08-26
Try this one-liner if storing results in a single file is acceptable:

```
find . -regex '.+.\(dic\|txt\|lst\)' -exec cat {} \; | sort | uniq > output_file.txt
```

It's a fast solution. I'm sure it can be done much more better. Anyway, I hope it will deal with such a huge amount of data like yours.

---

