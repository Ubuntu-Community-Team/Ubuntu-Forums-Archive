---
title: "Verifying that files excist from a text document?"
date: 2008-01-31
forum: General Help
---

### Post by SogniX on 2008-01-31
I have a text file of a list of a lot of files that I need to verify that they exist... they could be in various directories (actually I think in 2 directories), but it would be a pain to check them all one by one by hand. Then I need to log the result,
Here's a sample of what I've been doing so far:

$ ls /somedirectory/file1.txt 
/somedirectory/file1.txt 
$ ls /somedirectory/file2.txt
ls: /somedirectory/file2.txt No such file or directory

I would love if the results file looked like this:

/somedirectory/file1.txt 
ls: /somedirectory/file2.txt No such file or directory

so it's easy to see which files are missing. 
But I haven't a clue how to do this. :-(

Any help would be greatly appreciated! :-)

---

### Post by jw5801 on 2008-01-31
It depends on the format of the input file. If the input is purely a list of the files then:
```
cat /wherever/input | xargs -d "\n" ls
```
Should print out the list you want to standard out. To pipe it to a results file, you could use:
```
cat /wherever/input | xargs -d "\n" ls > /wherever/results
```

I'm am work at the moment rather than at a Linux box, so you'll just need to use "man xargs" to check that "-d" is the option used to define the end of each input. I'm working from memory but I'm pretty sure it's the right one. You could also make a list of only the files that are missing if you wanted:
```
cat /wherever/input | xargs -d "\n" ls | grep "No such file or directory" > /wherever/results
```
Should filter for only those that are missing (it should filter out everything that doesn't contain "No such file or directory" anyway, so if you have a file named that you'll get a false positive). Once again, check the "-d".

Actually, you won't need to check! Typing "man xargs" into google returns a copy of the manpage. Good to know! So yes, "-d" is the correct option for this situation.

---

### Post by SogniX on 2008-01-31
Thank you so very much! That did it! 

Altho, the > resultsfile didn't work, nothing was output to the file. 

But that's OK because I did see it on the screen and was able to copy and paste that into a new file. 

Thanks again! :-)

---

