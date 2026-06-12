---
title: "delete files by creation date"
date: 2007-11-27
forum: General Help
---

### Post by oneadvent on 2007-11-27
How do I delete a group of files based on their creation date?

---

### Post by erfahren on 2007-11-27
this might help a little
[http://www.linuxquestions.org/questions/linux-general-1/shell-script-to-remove-old-files-based-on-date-7368/](http://www.linuxquestions.org/questions/linux-general-1/shell-script-to-remove-old-files-based-on-date-7368/)

---

### Post by kebes on 2007-11-27
> **oneadvent said:**
> How do I delete a group of files based on their creation date?

On the commandline, you can use the "[find]("http://unixhelp.ed.ac.uk/CGI/man-cgi?find")" command to select certain files, and then use the "-exec" switch to cause some other command to be run on those files. So if you use "-exec rm" you will delete the files that are found. So, for example:
```
 find -mmin +4 -exec rm {} +
```
will delete any files in the current directory (and sub-directories) that are older than 4 minutes. This is because the "-mmin +4" switch causes find to return files older than 4 minutes. There are other options, like "-mtime" that return files based on modified date in days. You can use + or - depending on what kind of behavior you are trying to achieve. For a more complete explanation of all the options, see the manual page:
[http://unixhelp.ed.ac.uk/CGI/man-cgi?find](http://unixhelp.ed.ac.uk/CGI/man-cgi?find)

Be careful when using the **rm** command! It's usually a good idea to test your command first, before using it. So, for instance, use something like:
```
 find -mmin +4 -exec ls {} +
```
which will just list the files that you are selecting for. If the list looks right, then you can switch the "ls" to "rm" in the command and it will delete the files.


I hope that helps.

---

### Post by oneadvent on 2007-11-27
I did this:

```
find -type f -name "*.vox" -mtime +36 -exec rm {} \;
```

but it did not delete every *.vox file from before October 21st. 

What did I do wrong? Is it the file type?

Josh

---

### Post by oneadvent on 2007-11-27
Whew. The simplist problems are the hardest to solve. The command I used is correct. This is what is wrong:

```
ls -la >> /home/jwelch/vox.txt
```

I had used that two times, and as a result the file was getting bigger and bigger. The files were gone, It was just misrepresented. 

Ha, so I should have typed:

```
ls -la > /home/jwelch/vox.txt
```

or just picked a different file name.

(forgot to mention. The server that this was being run on really sucks so the output of an ls in this folder would have killed it.)

---

