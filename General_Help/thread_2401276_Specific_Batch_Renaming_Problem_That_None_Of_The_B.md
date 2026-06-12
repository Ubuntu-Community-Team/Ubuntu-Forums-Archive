---
title: "Specific Batch Renaming Problem That None Of The Batch Renamers Seem To Be Good For"
date: 2018-09-16
forum: General Help
---

### Post by raphaell2 on 2018-09-16
Hi Everyone, 

I have a problem with renaming a large number of files that none of the batch file renaming apps available under Synaptic seem to be good for. 

Namely, I have really a lot of files in really a lot of folders (which, themselves, are all in one larger folder), and I want each file to be renamed so that the name of the folder it is in becomes a file name prefix. 

i. e. '/foldername/filename' > 'foldername-filename'

Doing this per hand for each of the many files in the hundreds of folder would take very, very long. 
Any ideas?

---

### Post by TheFu on 2018-09-16
Write a bash script.  Use find, basename, dirname, sed, and mv.

Or
you could just use find and make a list of all the files to be renamed, then use editor techniques to make a 1-line-for-1-file mv command.  I do this all the time when less than 100 files are involved.

---

### Post by HermanAB on 2018-09-16
Did you look at the lesser known "Phatch" program?

---

### Post by raphaell2 on 2018-09-16
TheFu: 1. Sure, but I have no idea how to do that. 2. There are more than a thousand files. 

HermanAB: The website is down and the software isn't in the repos.

---

### Post by TheFu on 2018-09-16
1. simple bash scripting is a handy thing to know.

2. The fact that there's 5 or 10,000 doesn't really matter. 
** get the list of files first $ find . -type f > file.lst
** open that file in vim
** duplicate all the lines - put them at the bottom.
** search and replace all '/' for '-' for the 2nd half of the file
** visually select the 2nd half of the file with all the new names, cut those, then
** move to the top of the file, move the cursor to the far right enough that there aren't any characters anywhere in any lines there.
** use column paste
** do a global search and replace to insert 'mv ' on every line.

If you don't know exactly how to do the above, I'd practice on a file with only 5 files to get the hang of it. Knowing how to use an editor is a huge skill.

It took me longer to write that than it would have taken to actually do it.  If your editor can't do that, find a better editor. But it  would be faster than creating a script, debugging the script.  OTOH, if I needed to do this 2 or more times, then I'd definitely write the script.

---

### Post by raphaell2 on 2018-09-16
Thank you, that almost works - but when I try to execute the resulting script, I get a long list of error messages telling me that the intended target is not a directory.

---

### Post by raphaell2 on 2018-09-16
Ok, I inserted -T. It worked! Thank you again!

---

### Post by TheFu on 2018-09-16
> **raphaell2 said:**
> Ok, I inserted -T. It worked! Thank you again!

Selective and global search and replace can be very powerful, indeed.  Nano can't do these things easily.
For people without strong editor skills, you could try to use a spreadsheet tool for column-only  search and replace as well.

If this is solved, please use the "thread tools" button to mark it that way. This helps both people looking for solutions and prevents those hoping to help from wasting time.

---

