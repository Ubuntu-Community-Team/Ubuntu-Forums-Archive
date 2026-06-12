---
title: "[SOLVED] create files on the fly"
date: 2008-05-01
forum: General Help
---

### Post by tjajab on 2008-05-01
I wonder if there is a way to "stream" file data to applications that expect files as input? For example, if I want to look at a file in an application, but I first need to convert that file, can I avoid creating a temporary file? I mean, I could always do:
```
man2html somemanpage.gz > /tmp/averyunusualname.html && firefox /tmp/averyunusualname.html
```
, but then I would have to delete the file afterwards or it will take unnecessary space on my hard drive. What I am searching for is this tool:
```
man2html somemanpage.gz | somecoolfilyfiertool firefox
```
The somecoolfilyfiertool creates a temporary file from the input and stores it and removes it after the child process has finished ... :) There are no such tool, eh?

---

### Post by HermanAB on 2008-05-01
You are on the right track.

cat, |, tee, >, >>

and you can send output to /dev/null to make it disappear into a void.

Cheers,

H.

---

### Post by tjajab on 2008-05-02
I guess the problem is though, that programs that expects files as input parameters, actually expects *filenames* as input parameters, and there is no way to have a filename on some random data lying around in the computer memory? Or am I wrong, is it possible to pipe something to firefox that is not actually lying on a disk somewhere?

---

### Post by bingoUV on 2008-05-02
A file will not be really deleted until it is opened by firefox. In the light of this fact, modify your first line to : 
```

man2html somemanpage.gz > /tmp/averyunusualname.html && ( firefox /tmp/averyunusualname.html & ) && (sleep 5 ; rm -f /tmp/averyunusualname.html)

```The sleep 5 is for firefox to startup and open the file. Ideally it should have waited for firefox to open the file (man fuser) but I am lazy.

---

### Post by bingoUV on 2008-05-02
Of course you could delete the file on the exit of firefox. The above is in case you do not want to do it, maybe because you want the file to be deleted even before firefox is closed completely. e.g.
```

man2html somemanpage.gz > /tmp/averyunusualname.html && ( firefox /tmp/averyunusualname.html ; rm -f /tmp/averyunusualname.html & )

```

---

### Post by tjajab on 2008-05-02
Ok, thanks guys, here is my final filifier, called ff:

```

#!/bin/bash
# Some usage information
if [ "$#" -lt 1 ]; then
  echo "Usage: ff APPLICATION [TMPFILENAME]
        Converts stdin data to a file (with name TMPFILENAME) to be read by APPLICATION,
        and deletes the file once APPLICATION no longer accesses it."
  exit 1
fi
if [ "$#" -lt 2 ]; then
  FILENAME=/tmp/strangename
  if [ -e $FILENAME ]; then
    rm -f $FILENAME
  fi
else
  if [ -e $2 ]; then
    echo "File already exists. Please choose another filename."
    exit 1
  fi
  FILENAME=$2
fi
# Make terminal stdin, if possible:
PARENTTTY=`ps --no-headers --ppid $$ -o tty`
while read myline
do
  echo $myline >> $FILENAME
done
if [ -n $PARENTTTY ]; then
        $1 $FILENAME < "/dev/"$PARENTTTY
else
        $1 $FILENAME
fi
while fuser -s $FILENAME
do
  sleep 3
done
rm -f $FILENAME
exit 0

```

I guess I put some randomness into the filename to, but this is good enough.
I can now do:
man2html `man -w grep` | filifier firefox

Happiness! :)

---

### Post by tjajab on 2008-05-02
Now it almost works fine, I can for example do:
```
unzip -p tmp.zip | ff gedit
```
(ff is my script), but when I do
```
unzip -p tmp.zip | ff vim
```
vim says something about the input not coming from terminal, I can see the content of the uncompressed file in Vim, but when I close Vim the terminal goes bananas, so I have to write ```
reset
```. How come / can I do something about this?

---

### Post by bingoUV on 2008-05-02
when you pipe something to vim, its standard input no longer remains that of the terminal, but is now the output of unzip command. vim does not like this. You have 2 options : 
1. Use gvim. Easy but not so good.
2. In your script, when you start vim, read from standard input of the terminal. To do this, you will have to get the tty of the terminal from which the script was invoked.  Add the following line within your script. $$ is the pid of the shell process that is running your script ff.
```

ps -aef | grep $$ | grep -v grep

```This will give you a line like this. Parse it for the tty (man cut).
```

<username> 25728 12927  0 07:45 pts/19   00:00:00 /bin/bash ./test.sh

```The tty in the above example is "**pts/19**". Take this in variable $parentTty. Now the line where you start vim that currently is 
```

$1 $FILENAME

```change it to 

```

$1 $FILENAME < "/dev/"$parentTty

```

EDIT : 
Maybe ps can be given a flag to get only the tty of the specified process, but I am lazy.

---

### Post by tjajab on 2008-05-02
Works fine. I updated my script to reflect this change. It is starting to get useful :)

---

### Post by tjajab on 2008-05-02
I found out I could use
```
ps --no-headers --ppid $$ -o tty
```

---

