---
title: "copying/moving files of a certain filetype but have no extension"
date: 2016-03-18
forum: General Help
---

### Post by ragip on 2016-03-18
i have a directory consisting of files of two filetypes. the problem is i want one type of files moved or copied to another folder (or at least selected than deleted)
hate to write this but it is easy as ```
copy *.avi c:\target 
``` in msdos and i think there must be such an easy way that i cannot find
and i have seen some mini-scripts

---

### Post by bab1 on 2016-03-18
> **ragip said:**
> i have a directory consisting of files of two filetypes. the problem is i want one type of files moved or copied to another folder (or at least selected than deleted)
hate to write this but it is easy as ```
copy *.avi c:\target 
``` in msdos and i think there must be such an easy way that i cannot find
and i have seen some mini-scripts```
cp *.avi </path/to/dir>
``` Where <path/to/dir> is the directory you want the data copied to.

---

### Post by ragip on 2016-03-18
yes but there is no file with the extension. there are AVI files but they have no extension. that is the problem. 
at least a problem for an old windows user like me

---

### Post by bab1 on 2016-03-18
> **ragip said:**
> yes but there is no file with the extension. there are AVI files but they have no extension. that is the problem. 
at least a problem for an old windows user like me
Then why bring extensions up in your example?  It sounds like you want Linux to figure out what the file type is and copy that type only (copy by mime type).  This is not a simple line in some script.  As far as I know most common Linux command line tools don't distinguish files by mime types unless they are dedicated to a specific job (e.g xdg-mime).

---

### Post by ragip on 2016-03-18
well, i guess i am used to work with extensions and wanted to do it same way, and it seems linux indeed figures out the filetype but do not let me selectively copy it. but thanks for the help because i can now google for "copy by mime type" and look for the answer

---

### Post by bab1 on 2016-03-18
> **ragip said:**
> well, i guess i am used to work with extensions and wanted to do it same way, and it seems linux indeed figures out the filetype but do not let me selectively copy it. but thanks for the help because i can now google for "copy by mime type" and look for the answer

[**This**]("http://unix.stackexchange.com/questions/176157/how-to-check-the-file-type-in-a-script") is an example of checking for mime types in a BASH script.  BASH is the command line interpreter (like Windows Power Shell).

---

### Post by HermanAB on 2016-03-18
The utility called 'file' can be used to figure out what a file type is.

file tests each argument in an attempt to classify it.  There are three sets of tests, performed in
     this order: filesystem tests, magic tests, and language tests.  The first test that succeeds causes the
     file type to be printed.

Read the man page for details, then make a script using a combination of 'find', 'file' and 'cp'.

---

### Post by ragip on 2016-03-21
thanks, now i figured it out

---

