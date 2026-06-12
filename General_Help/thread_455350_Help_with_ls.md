---
title: "Help with ls"
date: 2007-05-26
forum: General Help
---

### Post by TeeAhr1 on 2007-05-26
Doing a little spring cleaning around here, hoping someone can help me out with this.

I'm looking for a way to list all the files in a directory (recursively) that are not .mp3, .flac, or .ogg files.  I looked at the ls man page, and found an option -I, but trying "ls -I=*.mp3 -R /path/to/music/" didn't do it.  What am I doing wrong?  Thx, as always...

-p.

---

### Post by Pragmatist on 2007-05-26
```
ls -I *.mp3 -I *.flac -I *.ogg
```

---

### Post by Pragmatist on 2007-05-26
In other words, you use -I and then a space and then your pattern.  So, to follow your example, it would be:

ls -I *.mp3 -I *.flac -I *.ogg -R /path/to/music

You don't need the '=' and you always put a space between the switch (-R or -I  etc...etc...) and the argument (*.mp3  /path/to/music  etc...etc...)

---

### Post by stylishpants on 2007-05-26
While the above solution is correct, it has the disadvantage that it lists all the directory names as well, resulting in lots of irrelevant output and blank lines for a large directory tree.

If you want just a list of files, something like this is probably better:

```
find /path/to/music/ -type f | grep -v ogg$ | grep -v flac$ | grep -v mp3$
```

---

### Post by earobinson on 2007-05-26
both soultions should work, I like soultion 2 better.

Note: you can man any of the commands for more info on how they work ```
man command
```

---

### Post by Pragmatist on 2007-05-26
I also like solution 2 better!  At least for recursive searching.  I'm glad I subscribed to this thread as it reminded me that I should finally learn the "find" command!  I've just been too lazy to learn all the syntax and have instead just used "locate".  However, "find" is a more flexible tool if you know what your doing (and you don't have to always update a database as you do with "locate").

---

### Post by earobinson on 2007-05-26
yup being able to subscribe to threads is the best way to learn. (I get corrected all the time)

---

### Post by pmg on 2007-05-26
The** find **command is a good friend to have.  I also use **du -a** alot for things like this.  It gives size info as well so that lets me concentrate on bigger files, and so I can focus on where I'll get the most space back, but it's not as powerful as find.  

However, I will clean up the suggested command a bit as follows...
```
find /path/to/music/ -type f | grep -v -e \\.ogg$ -e \\.flac$ -e \\.mp3$
```
(Why use three grep's when one will do, and the original command would have removed files from the list that ended with e.g "mp3" and not "**.**mp3" as was requested.)

---

### Post by Pragmatist on 2007-05-27
> **pmg said:**
> The** find **command is a good friend to have.  I also use **du -a** alot for things like this.  It gives size info as well so that lets me concentrate on bigger files, and so I can focus on where I'll get the most space back, but it's not as powerful as find.  

However, I will clean up the suggested command a bit as follows...
```
find /path/to/music/ -type f | grep -v -e \\.ogg$ -e \\.flac$ -e \\.mp3$
```(Why use three grep's when one will do, and the original command would have removed files from the list that ended with e.g "mp3" and not "**.**mp3" as was requested.)

Just for my own edification, I tried this out and read a bit about regular expressions.  This command gives me the same results with one '\' rather than two '\\'

```
find /path/to/music/ -type f | grep -v -e \.ogg$ -e \.flac$ -e \.mp3$
```

If I'm missing something please let me know.  As I understand it, the forward slash is to escape characters so they are treated literally.  Thus, the period has a special meaning, but when escaped \. it is treated as just a period (which is what we want as we are excluding certain extensions, and extensions begin with a period).  What is the first slash for?

---

### Post by stylishpants on 2007-05-27
Hey, if we're golfing we can go even farther than that.

```
find /data/music/main -type f | egrep -v '\.(ogg|flac|mp3)$'
```

Or you can eliminate the grep altogether:

```
find /data/music/main -regextype posix-egrep -type f ! -regex ".*\.(mp3|ogg|flac)$"
```

I do not recommend that last one though because it won't handle non-ascii characters in the filenames properly.   For example, a filename like this:
```
Suzanne Vega - 99.9 F° - 04 - 99.9 F°.ogg
```
will get returned even though it ends with .ogg,  The problem is that the first . in the regexp won't match that funny ° character.

Anyway, your question:

> 
If I'm missing something please let me know. As I understand it, the forward slash is to escape characters so they are treated literally. Thus, the period has a special meaning, but when escaped \. it is treated as just a period (which is what we want as we are excluding certain extensions, and extensions begin with a period). What is the first slash for?



When you use only a single backslash (it's not a forward slash), the shell uses it to escape the . character, so \. just evaluates to . before the find command even sees it.  Thus, from the find command's point of view, it's not a \. at all, it's just a . character.

If this is unclear, you should be able to illustrate this to yourself by experimenting with "echo":
```

echo .
echo \.
echo \\.

```

Anyway, that's why you need the first of the two backslashes: the first backslash escapes the second backslash, so find will actually see the characters \. when it runs.

To avoid needing lots of backslashes in your regexps, you usually single quote them.  The shell doesn't mess with things you put in single quotes.


As for the reason why you are getting the same results whether you use one or two slashes, that depends on the set of files you're scanning.  For most people's music collection, it will make no difference whether the . has its literal meaning, or its wildcard meaning, because most people won't have files that end with one of those extensions preceded by a non-dot character.

If you make filenames like this and retest, you should see a difference:
```

file.mp3
file_mp3

```

---

### Post by pmg on 2007-05-27
The grep command takes a regular expression in which the . character matches any one character.  $ matches the end of a line, so "grep .mp3$" matches any char followed by "mp3" at the end of a line.  It wouldn't be much different than "grep mp3$".  You tell grep to match the . character by escaping it with a backslash, except \ is a shell metacharacter and so with "grep \.mp3$" the shell itself eats the \ and all grep sees is ".mp3$".  In order to escape the \ from the shell so it is passed thru to grep, we need to escape *it* with a \, hence the double \.  You see can this with the echo command:

```
$ echo \\.mp3$
\.mp3$
```

will show what passes thru the shell and gets to the grep command.

As a side note, $ is also a shell metacharacter.  It is used to indicate a shell variable.  However the shell is smart enough that if it's followed by white space, the shell just passes it thru.  If the $ was followed by another character it would need to be escaped also.  Not all shells do this.  csh, for example, doesn't pass thru $ this way, so if the command was entered in csh (or tcsh) all $'s would need to be escaped also.

---

### Post by Pragmatist on 2007-05-27
So, getting back to the OP (I feel a little guilty inciting this somewhat tangential discussion :) ), what would be the shortest command expression to accomplish the OP's goal?

Here is my summary:  From what I've read so far, the cleanest solution seems to be the one given by stylishpants:
```
find /data/music/main -type f | egrep -v '\.(ogg|flac|mp3)$'
```I think the solution I offered, using the ls command, works.  However, the output is messy and harder to read than the above solution.  Also, the above solution avoids repeating commands  (such as grep) and/or switches (-I  and -e)  It is compact, and, also, it quotes the expression which is accurate and best practice.

---

### Post by TeeAhr1 on 2007-05-27
Neat!  I did what I was trying to with the first command that Pragmatist gave, but this has been an interesting thread, thanks for the edumacation!

-p.

---

