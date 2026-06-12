---
title: "Create a tar file for each subdirectory in a given directory"
date: 2022-05-01
forum: General Help
---

### Post by demonenero84 on 2022-05-01
Hi there,
I wanted to create tar files, specifically one for each directory so I googled and I found this command 
```
[FONT=monospace][FONT=monospace]find . -maxdepth 1 -mindepth 1 -type d -exec tar cvf {}.tar {}  \;
[/FONT][/FONT]
```[FONT=monospace]
This one works but my directories are contained in a folder named "." , so let's say my folder is named 1 a get a tar file which contains a folder named . and inside a folder named 1.
Is there any way to simply remove this "." folder in my tar files?
thanks a lot in advance
[/FONT]

---

### Post by &amp;KyT$0P# on 2022-05-01
You need to strip off the leading [FONT=Courier New]./[/FONT] in the arguments passed to [FONT=Courier New]tar[/FONT].

One way would be to write a shell script, something like -
```
#!/bin/bash
folderToTar="$(echo "$1" | sed -r -e 's#^\./##g')"
tar -cvf "$folderToTar".tar "$folderToTar"
```
Then have your [FONT=Courier New]find[/FONT] command exec that script instead.

---

### Post by TheFu on 2022-05-01
Use a **find** command that doesn't find '.'?  
```
$ find [a-Z0-9]* -maxdepth 1 ....
```

Do you realize that tar will recursively include sub-directories?
If the files are already compressed (images, music, videos), then **tar jcvf** will add some compression. Just use the 'j' option with the de-tar command too.

---

### Post by demonenero84 on 2022-05-01
Thanks
So I made a script like the one you posted, I called it 01.sh and made it executable, what should I do next?
> [FONT=monospace][FONT=monospace]
find . -maxdepth 1 -mindepth 1 -type d -exec /home/username/01.sh \;[/FONT][/FONT]

If I do that I get this message
> 
[FONT=monospace][COLOR=#000000]tar: Substituting `.' for empty member name [/COLOR]
tar: : Cannot stat: No such file or directory 
tar: Exiting with failure status due to previous errors
[/FONT]
What am I doing wrong?
thanks a lot

---

### Post by demonenero84 on 2022-05-01
> **TheFu said:**
> Use a **find** command that doesn't find '.'?  
```
$ find [a-Z0-9]* -maxdepth 1 ....
```

Do you realize that tar will recursively include sub-directories?
If the files are already compressed (images, music, videos), then **tar jcvf** will add some compression. Just use the 'j' option with the de-tar command too.

thanks a lot for the reply, yes I want a file that contains every sub-directory

Edit: It works just like I wanted but I wanted to know what I did wrong with the script solution

Edit 2 : It does not work with directories that start with letters ( it works only if they start with numbers)

---

### Post by &amp;KyT$0P# on 2022-05-01
> **demonenero84 said:**
> Edit: It works just like I wanted but I wanted to know what I did wrong with the script solution

The script takes one filename on its command line, but you also removed the {} from your find command, so the script didn't receive the filename and ran the commands with an empty string instead.  You needed replace only [FONT=Courier New]tar cvf {}.tar[/FONT] with [FONT=Courier New]/home/username/01.sh[/FONT]

---

### Post by TheFu on 2022-05-01
> **demonenero84 said:**
> Edit 2 : It does not work with directories that start with letters ( it works only if they start with numbers)

Try
```
$ find [a-zA-Z0-9]* .... 
```

There are different globbing/regex engines, each with differences. I mostly use egrep and perl RE engines. Bash has something called globbing.  In perl, I could use '^[:IsAlnum:]?.*' as a pattern match to get exactly this.  My bash globbing-fu is not as strong.

---

### Post by demonenero84 on 2022-05-01
thanks a lot guys

---

