---
title: "Moving Files Between Subdirectories"
date: 2023-05-30
forum: General Help
---

### Post by wyattwhiteeagle on 2023-05-30
What am I missing here?
What am I doing wrong?

```
find /home/wyatt/Desktop/Test-Folder/Test-Dir-1/* -type f '*.txt' -print0 | xargs -0 mv -t /home/wyatt/Desktop/Test-Folder/Test-Dir-2/TXT
```

I ran the above command line and got the following...

```
find: paths must precede expression: `*.txt'
mv: missing file operand
Try 'mv --help' for more information.
```

I've been working on this command for quite some time now.

Avoiding the "current working directory", I'm wanting to move files within subdirectories into subdirectories within another desktop folder.
I'm using a small test directory with copied files.

I checked the manual's, it seem's they just cause me more confusion.
I've checked all of the following links for commands and idea's.
It seem's I "just can't get it through my thick head"

[https://unix.stackexchange.com/questions/572594/how-to-remove-many-files-of-similar-names](https://unix.stackexchange.com/questions/572594/how-to-remove-many-files-of-similar-names)
[https://stackoverflow.com/questions/17334014/move-files-to-directories-based-on-extension](https://stackoverflow.com/questions/17334014/move-files-to-directories-based-on-extension)
[https://askubuntu.com/questions/443830/delete-all-files-whose-filenames-contain-a-particular-string](https://askubuntu.com/questions/443830/delete-all-files-whose-filenames-contain-a-particular-string)
[https://tecadmin.net/delete-files-older-x-days/](https://tecadmin.net/delete-files-older-x-days/)
[https://stackoverflow.com/questions/17334014/move-files-to-directories-based-on-extension](https://stackoverflow.com/questions/17334014/move-files-to-directories-based-on-extension)
[https://unix.stackexchange.com/questions/67503/move-all-files-with-a-certain-extension-from-multiple-subdirectories-into-one-di](https://unix.stackexchange.com/questions/67503/move-all-files-with-a-certain-extension-from-multiple-subdirectories-into-one-di)
[https://unix.stackexchange.com/questions/394752/how-to-move-files-from-certain-directories-to-newly-created-directories-based-on?rq=1](https://unix.stackexchange.com/questions/394752/how-to-move-files-from-certain-directories-to-newly-created-directories-based-on?rq=1)
[https://unix.stackexchange.com/questions/67503/move-all-files-with-a-certain-extension-from-multiple-subdirectories-into-one-di#](https://unix.stackexchange.com/questions/67503/move-all-files-with-a-certain-extension-from-multiple-subdirectories-into-one-di#)

---

### Post by Holger_Gehrke on 2023-05-30
You're missing an option before '*.txt' - probably '-name' or '-iname'. Without that option find interprets '*.txt' as another path you want to search, but all paths need to come before tests or actions and therefore find gives an error and no results, therefore xargs has nothing to feed into mv and then mv produces an error because there are to few parameters - there need to be at least two.

Holger

---

### Post by wyattwhiteeagle on 2023-05-30
> **Holger_Gehrke said:**
> You're missing an option before '*.txt' - probably '-name' or '-iname'. Without that option find interprets '*.txt' as another path you want to search, but all paths need to come before tests or actions and therefore find gives an error and no results, therefore xargs has nothing to feed into mv and then mv produces an error because there are to few parameters - there need to be at least two.

Holger


Thank you
Adding -name into the mix did the trick...
```
find /home/wyatt/Desktop/Test-Folder/Test-Dir-1/* -type f -name '*.txt' -print0 | xargs -0 mv -t /home/wyatt/Desktop/Test-Folder/Test-Dir-2/TXT
```


There's times when I get the "will not overwrite" message.


Where in that command line would '--backup=numbered' best fit?

---

### Post by Holger_Gehrke on 2023-05-30
Anywhere after mv is good but not in between '-t' and the path.

By the way, the difference between -name and -iname is case sensitivity, so if there are '*.TXT' flies in there you want to move then '-iname' is the better choice.

Holger

---

### Post by wyattwhiteeagle on 2023-05-30
> **Holger_Gehrke said:**
> Anywhere after mv is good but not in between '-t' and the path.

By the way, the difference between -name and -iname is case sensitivity, so if there are '*.TXT' flies in there you want to move then '-iname' is the better choice.

Holger

Thank you

I'll "tweak" the command and let ya know how it goes.

---

### Post by wyattwhiteeagle on 2023-05-30
```
find /home/wyatt/Desktop/Test-Folder/Test-Dir-1/* -type f -iname '*.txt' -print0 | xargs -0 mv --backup=numbered -t /home/wyatt/Desktop/Test-Folder/Test-Dir-2/TXT
```


That worked.
Is there a way to have it put the number before the '.txt'?

---

### Post by Holger_Gehrke on 2023-05-30
Not with the 'mv' command itself. But you can run a rename afterwards:
```

rename 's/txt\.~(.*)~$/~$1~.txt/i' *

```
The part in single quotes is a Perl expression; the 's' means substitute, the slashes are separators, the part between the first and second slash is the text to search for, the part between the second and third slash is the replacement, and the trailing 'i' is an option meaning 'case insensitiv'. The "text to search for" is a regular expression; most characters in RE stand for themselves, the exceptions (in this one) are '.' (which stands for one arbitrary character), '\' (takes away any special meaning from the following character, so '\.' means a literal '.' and **not **an arbitrary character, '*' (a quantifier meaning as many of the previous character as can be found; '.*' means as many (including 0) arbitrary characters as there are), '$' (meaning 'end of input'), and the parentheses are for grouping sub-expressions and remembering them (so the sub-expression can be used in the replacement; '"$1", "$2", "$3" ... stand for the first, second, third sub-expression in parentheses.

Holger

---

### Post by wyattwhiteeagle on 2023-05-30
> **Holger_Gehrke said:**
> Not with the 'mv' command itself. But you can run a rename afterwards:
```

rename 's/txt\.~(.*)~$/~$1~.txt/i' *

```
The part in single quotes is a Perl expression; the 's' means substitute, the slashes are separators, the part between the first and second slash is the text to search for, the part between the second and third slash is the replacement, and the trailing 'i' is an option meaning 'case insensitiv'. The "text to search for" is a regular expression; most characters in RE stand for themselves, the exceptions (in this one) are '.' (which stands for one arbitrary character), '\' (takes away any special meaning from the following character, so '\.' means a literal '.' and **not **an arbitrary character, '*' (a quantifier meaning as many of the previous character as can be found; '.*' means as many (including 0) arbitrary characters as there are), '$' (meaning 'end of input'), and the parentheses are for grouping sub-expressions and remembering them (so the sub-expression can be used in the replacement; '"$1", "$2", "$3" ... stand for the first, second, third sub-expression in parentheses.

Holger

Is that for the "current working directory" only?
Is it for one file only, thus repeating the line for each file to rename?

---

### Post by Holger_Gehrke on 2023-05-30
The way it's written it's for all files in the current directory. That's what the '*' at the end of the command means; you could instead give an exact filename or a list of filenames or a glob that matches specific files; only files which match the RE will be renamed, so using '*' is safe if the expression is specific enough.  I wouldn't be surprised at all if there was some really tricky and smart way to make rename recurse through a directory hierarchy using only a very clever RE, but if there is one I don't know it.

You could of course use 'find' again to recurse through all directories
```

find . -type d -print -execdir bash -c 'rename -n '\''s/txt\.~(.*)~$/~$1~.txt/i'\'' *' \;

```
The '-print' is in there to get some feedback on where find currently is; the '-n' makes rename just print out what it would do (it prints "rename(<oldname>,<newname>)" for each file it would rename) - it's basically a 'dry-run' to check that it doesn't do anything horrible. I strongly advise letting this dry-run happen, since I don't have any numbered backup-files lying around in a deep hierarchy and couldn't really test this. After you're sure everything works as intended, do a second run without the '-n' in the rename-command.

Calling bash through '-execdir' is necessary to make the glob / wildcard '*' work right; globs are processed by the shell after you hit enter but before execution of the command starts by turning them into a list of filenames matching the glob. If you wrote "find . -type d -print -execdir rename -n 's/txt\.~(.*)~$/~$1~.txt/i' * \;' instead, the '*' would get replaced with a list of files by the shell after you hit enter so rename would try to rename the filenames from the starting directory in each subdirectory; if you escaped the '*' with a backslash or by having it in single quotes to stop the shell from expanding the glob, then rename wouldn't know what to do with the '*' since it expects the shell to handle wildcards. It would probably look for a file named literally '*' and fail.

Holger

---

### Post by wyattwhiteeagle on 2023-05-30
Will you please explain how a "dry-run" of this nature works?

I know how a simulated install works.
Is a command dry-run similar, or are there differences?

---

### Post by Holger_Gehrke on 2023-05-30
It's the same thing. I call it that since apt actually has a long option '--dry-run' for the short option '-s' which does something similar to what the '-n' (or the long option '--nono') does with rename: it tells you what it would do but doesn't do anything. That's good if you're not entirely sure that you've got all the options and parameters exactly right.

An example
```

holgeh@machine:~/Dokumente$ ls *.DOC
Brief.DOC
holgeh@machine:~/Dokumente$ rename -n 's/.DOC$/.doc/' *.DOC
rename(Brief.DOC, Brief.doc)
holgeh@machine:~/Dokumente$ ls *.DOC
Brief.DOC
holgeh@machine:~/Dokumente$ rename 's/.DOC$/.doc/' *.DOC
holgeh@machine:~/Dokumente$ ls *.DOC
ls: Zugriff auf '*DOC' nicht möglich: Datei oder Verzeichnis nicht gefunden

```
With the '-n' option rename shows what it would do but doesn't do it. Once I'm certain that it does what I want, I run the same command but without the '-n' and 'rename' does what it said it would do but in the best Unix tradition is quiet about what it does.
Holger

---

### Post by wyattwhiteeagle on 2023-05-30
oh wow...awesome.
thank you so much for all your help
it really helps

I need to take about a 2 or 3 day break to tend to responsibilities here around the house paying bills and groceries, etc

In my off time I'll work with it and post the results in 2 or 3 days

Again,
Thanks so much

---

### Post by TheFu on 2023-06-06
> **wyattwhiteeagle said:**
> Will you please explain how a "dry-run" of this nature works?


```
$ man rename
...
       -n, --nono
               No action: print names of files to be renamed, but don't rename.

```

Your system has manpages too.

---

### Post by wyattwhiteeagle on 2023-06-07
Using the terminal, how would I rename a file within a desktop subdirectory to a part of a single line within the same file?

I have a file named "abcdef.txt"
Line 10 within "abcdef.txt" says "Read Jousting-101".
My desired result in this is the filename to be "abcdef-Jousting-101.txt"

---

### Post by TheFu on 2023-06-07
So, you want to read a specific line from each file and use that line in the new name of the file?  Are there any common tags in all the files that are unique to the line with the desired filename?  If so, the a little bash script with **egrep** and **mv** can do it.  For something like this, you really need to code it yourself.  
[https://tldp.org/LDP/abs/html/](https://tldp.org/LDP/abs/html/) is the reference I'd use.

Pseudo-code, 
```
For each file in the input glob, 
   find the line with the specific title you want.  Remove any unwanted parts from it and save that into a $variable.
   If you want to retain the stuff after the period, save that to another variable, say $ext
   move $file $file-variable.$ext   # Unix spells rename, "mv"
Next file
```

Those would be the comments I put into the file BEFORE starting to code anything. Then I just need to create the commands that do what the comments say.  I'll leave that as an exercise for you.  I think it is 10 lines or less.

---

### Post by wyattwhiteeagle on 2023-06-08
I recently had to use PhotoRec to recover data from a flashdrive.
TestDisk worked, but didn't recover all my files.
I was able to give the files the proper permissions for being in the /home directory.
But the filenames are photorec's rendition.

PhotoRec has renaming code (not rename but creating "hard links").
I had already moved the files and changed the permissions before I became aware of that.

I need to add something into all my custom files that would make things easier for when I encounter this.
Like maybe on line 3.
This is a good exercise for me, but (for the time-being) it's probably easier to just go through each individual file changing the names.

The following isn't the same throughout all of the recovered files.
I use the same pattern in all my custom script's.
Line 4 and line 7 have the desired original filename.
These are the only "common" things in all my scripts.
```

#!/bin/bash

# Change permissions
# chmod a+x /home/wyatt/Desktop/Custom-Script-1.sh

# Run the script
# /home/wyatt/Desktop/Custom-Script-1.sh

```

---

### Post by TheFu on 2023-06-08
> **wyattwhiteeagle said:**
> I recently had to use PhotoRec to recover data from a flashdrive.
TestDisk worked, but didn't recover all my files.
I was able to give the files the proper permissions for being in the /home directory.
But the filenames are photorec's rendition.
 

You do realize that if you have backups, none of that is needed.  The filenames are saved in the backups. No need to testdisk or photorec, which are far from 100%.  Often, I only get back 50% of the files I want.  Yep. Backups are much, much, easier.

---

### Post by wyattwhiteeagle on 2023-06-08
> **TheFu said:**
> You do realize that if you have backups, none of that is needed.  The filenames are saved in the backups. No need to testdisk or photorec, which are far from 100%.  Often, I only get back 50% of the files I want.  Yep. Backups are much, much, easier.
Oh yeah, what is a "$variable"?

Yep, I realize it.

In fact, that's where I'm "muckin-up" in my computing practice's.
If performing a fresh clean OS install is gonna' "muck up" my flashdrives, a backup to a flashdrive isn't good at all.

For me, creating scripts can be difficult, especially where options, expressions, and arguments are concerned.
In one, an option may be an argument in another.

Back some time ago, I seen a thread where you and Paddy are talking about the "standards" of mounting to the media directory.
It details at what lengths Canonical went to render the details of those "standards".
[https://ubuntuforums.org/showthread.php?t=2473833](https://ubuntuforums.org/showthread.php?t=2473833)

I know there are better practices.
Most of them are at a recurring financial cost at an "outstanding" amount for someone on a fixed monthly low income.
$20 doesn't seem like much, but when one is counting pennies on the 5th of every month...$20 is a lot.

Do you know about the system monitoring tool "Monitorix"?

Not trying to remind of old "bad blood", but...
Part of my computing practices involve searching for better storage and backup alternative's.
I have other threads here that go into in-depth info concerning each of those.
You know of most of them.

---

### Post by Holger_Gehrke on 2023-06-10
> **wyattwhiteeagle said:**
> Oh yeah, what is a "$variable"?
[...snip-snap...]

The shell is quite a complete programming language, so of course it has variables - named pieces of memory in which you can store whatever information you want. You define a variable with 'name=value' (no spaces around the '='; if you have a space before it, the shell tries to execute the name; if you have a space after it, it defines an empty variable and tries to execute the value). To use the value of a variable you write '$name' or '${name}. The latter variation is needed when you use array variables (the brackets used for the index into the array would be interpreted as a wildcard if the braces weren't there) or write a script or a function with more than 9 positional parameters (${11} is the eleventh positional parameter, $11 is the first positional parameter followed by a '1'). A small example:
```

#!/bin/bash

# count files in the current directory

declare -a filelist                 # filelist is an array; since the next line works only for arrays the shell would be smart enough to define it as one, but I like to be explicit when scripting ...
filelist=(*)                        # read the names of the files in the current working directory into the array
echo ${#filelist
[*]}                # parameter expansion, number of elements in the array

```
Variables are local to the shell in which you define them. If you want the shell to pass a copy of the variable to it's child processes you have to use 'export name'.
There are are quite a few variables which are already defined by the system for example PATH, USER, HOME, PWD. Then there are 'magic' variables which do something special like _ (the last command executed), ? (the exit code of the last command), RANDOM (gives a random number between 0 and 32767, a different one each time you use it), and many more.
You can see a list of the currently defined variables with 'declare -p' which will print the names, attributes and values of all variables currently defined in the shell. You can also use 'env' to get a list of the exported variables.
There's a lot more to say about this topic. You can either read the relevant chapters in 'The Linux command Line" or try to make sense of the bash manual page (which "The Linux Command Line" calls "The Most Brutal Man Page Of Them All" - and Mr. Shotts has a point there, it's dense as lead and really meant as a reference for people who know bash quite well already).

Holger

---

### Post by TheFu on 2023-06-10
> **wyattwhiteeagle said:**
> Oh yeah, what is a "$variable"?
bash supports storing a value inside a variable, like we learned in 8th grade algebra - solve for "X".

> **wyattwhiteeagle said:**
> 
If performing a fresh clean OS install is gonna' "muck up" my flashdrives, a backup to a flashdrive isn't good at all.


Flash drives shouldn't be used for anything other than moving files via sneaker*net.  Definitely NOT for backups.
A 2TB external HDD is $20-$40 these days.  That should be able to hold all the needed backups for any house, except huge media files.  I've been backing up 15 systems to a 1.5TB external 3.5" HDD for almost a decade. I'm completely serious.
```
$ df -Th /Backups
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdf1      ext4  1.4T  1.3T   32G  98% /Data/1.5T
```

> **wyattwhiteeagle said:**
> 
I know there are better practices.
Most of them are at a recurring financial cost at an "outstanding" amount for someone on a fixed monthly low income.
$20 doesn't seem like much, but when one is counting pennies on the 5th of every month...$20 is a lot.

I dislike recurring subscriptions too, so I have a little personal fund for computer stuff that I pre-pay into.  My next purchase being saved for are for (2) 8+TB HDDs to I can retire (4) [or more] old 2TB HDDs that are 10 yrs old.  I'm looking for reputable HDDs with 5 yr warranties that aren't from 1 specific vendor whose drives and management has failed me too many times to ever trust again.  Management lied about design faults for over a year once, then it became obvious when their HDD failure rate for over 2x higher than everyone else's that it was a design flaw.  One time, about 5 yrs after those lies, I gave them a chance again and had (2) 2TB drives fail right at 1 yr of use.  I have other vendor drives last 5, 8, 10, 13 yrs (so far).  For me, life is too short to deal with companies that lie.
I need larger HDDs to keep the number of SATA/eSATA ports lower.  Seems newer motherboards come with just 4 SATA ports and not 6 like my prior systems all had.  Plus, if I use an m.2 SATA SSD, I lose access to 2 of those 4 SATA ports.  Sometimes life just sucks.  I plan to pull the m.2 SATA SSD from that system and put it into an external USB3.2 enclosure.  I need to add that to my online shopping list.

---

