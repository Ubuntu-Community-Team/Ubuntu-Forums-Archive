---
title: "Help with &quot;for&quot; &quot;while&quot; commands"
date: 2013-02-15
forum: General Help
---

### Post by spiritech on 2013-02-15
hi

i understand how to do a for loop that reads the paths in a folder. i was wondering how i could do the same for paths in a file instead of reading the paths directly from the folder. 

i have a feeling it would be done using the while read command, however i am not familiar with the command and am not sure how to put it into practice.

my guess is below and also shows a rough idea of what i am trying to achieve.

while read FILENAME
  do echo $linefromfile | sed 's/$/new/'; done

exit

the intent of above would be to echo each line of the file one by one then exit.

spiritech

---

### Post by steeldriver on 2013-02-15
If the file paths are listed one-per-line in a file called 'file', you should be able to do something like

```
while read -r path; do echo "$path"; done < file
```If the paths are delimited by something other than newlines you can adjust the read command with a '-d' switch to set the delimiter

---

### Post by spiritech on 2013-02-16
> **steeldriver said:**
> If the file paths are listed one-per-line in a file called 'file', you should be able to do something like

```
while read -r path; do echo "$path"; done < file
```If the paths are delimited by something other than newlines you can adjust the read command with a '-d' switch to set the delimiter


thank you for your help i will try this. to help understand a little more what does the -r option do. also when using while read command does the file always go at the end  like  ```
< file
```also i have done this tutorial to start learning bash. [http://linuxconfig.org/Bash_scripting_Tutorial](http://linuxconfig.org/Bash_scripting_Tutorial) any advice on where to go next, especially with help on better understanding how to use, while 'for' 'if' 'else' 'functions' etc. i am also reading through the awk language.

---

### Post by steeldriver on 2013-02-16
Here is a pretty thorough reference --> [http://tldp.org/LDP/abs/html/internal.html](http://tldp.org/LDP/abs/html/internal.html)

You can also use the bash manual page [FONT=Courier New]man bash[/FONT]

Basically the '-r' switch tells the read command to treat backslashes as literals rather than parts of an escape sequence. It may not be necessary in this instance but for example if you had pathnames on a Windows share they might use \ as a path separator.

The ' < file ' part is a standard redirect that tells the shell to take its input from the named file instead of interactively from the standard input stream - i.e. instead of expecting you to type a list of paths

You can of course replace the  [FONT=Courier New]echo "$path"[/FONT] expression with any expression of your choice to do something with the value of "$path"

Hope this helps

---

### Post by schragge on 2013-02-16
> **spiritech said:**
> echo $linefromfile | sed 's/$/new/'
Since *sed* works line-wise, there's no much sence in reading file line by line, then feeding each line to *sed* separately. The same can be achieved with
```

sed 's/$/new/' file

```

---

### Post by spiritech on 2013-02-16
> **schragge said:**
> Since *sed* works line-wise, there's no much sence in reading file line by line, then feeding each line to *sed* separately. The same can be achieved with
```

sed 's/$/new/' file

```

yes. it was just an example.

---

### Post by spiritech on 2013-02-16
> **steeldriver said:**
> Here is a pretty thorough reference --> [http://tldp.org/LDP/abs/html/internal.html](http://tldp.org/LDP/abs/html/internal.html)

You can also use the bash manual page [FONT=Courier New]man bash[/FONT]

Basically the '-r' switch tells the read command to treat backslashes as literals rather than parts of an escape sequence. It may not be necessary in this instance but for example if you had pathnames on a Windows share they might use \ as a path separator.

The ' < file ' part is a standard redirect that tells the shell to take its input from the named file instead of interactively from the standard input stream - i.e. instead of expecting you to type a list of paths

You can of course replace the  [FONT=Courier New]echo "$path"[/FONT] expression with any expression of your choice to do something with the value of "$path"

Hope this helps

yes. thank you it helps a lot.

---

### Post by spiritech on 2013-02-16
i wonder how i could add i variable to the script, and for each time it reads the next line the variable could be changed. the variable being a number. maybe thats what functions are for.

---

### Post by steeldriver on 2013-02-16
Actually there's quite a lot of native arithmetic functionality in modern versions of bash e.g. you can create and increment an integer variable easily

```
$ n=0; while read -r filename; do echo $((n+=1)) : "$filename"; done < filelist
1 : /path/to/file
2 : /path/to/other/file
3 : /other/path/to/file
4 : \\path\to\Windows\share

```

---

### Post by spiritech on 2013-02-16
> **steeldriver said:**
> Here is a pretty thorough reference --> [http://tldp.org/LDP/abs/html/internal.html](http://tldp.org/LDP/abs/html/internal.html)


The ' < file ' part is a standard redirect that tells the shell to take its input from the named file instead of interactively from the standard input stream - i.e. instead of expecting you to type a list of paths

so just to be sure if did want to type a list of paths i would have to use the 'for f in' command?

---

### Post by schragge on 2013-02-16
You *can* use *for*, provided that the file names are properly quoted if they contain spaces or other unusual characters.

---

