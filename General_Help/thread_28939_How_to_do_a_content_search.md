---
title: "How to do a content search?"
date: 2005-04-22
forum: General Help
---

### Post by bk452 on 2005-04-22
Ok guys. Yesterday you got me hooked on searching for files using locate in the terminal.  What is the command for doing a content search?  I've been to all the info pages but when I follow the instructions I get a list of files so long I know that I'm doing it wrong.

I only need to search one directory, not the whole pc.  And does locate search the content of pdf files?

---

### Post by heimo on 2005-04-22
grep
```
 rgrep -s keyword *
``` 
-s = do not show errors (silent)
rgrep = grep -r (recursive, include subdirectories)
 
Most of the time I use it to just grep output of other programs - like
```
 lsmod | grep snd
``` 
 
To find files that match certain name, or attributes (like date of creation), use find. For example something like (sorry for all the errors, I can't test these at the moment):
 
```
 
for name in $(find -type f -max-depth 2 -iname '*txt'); 
  do cat $name >> all; 
done

``` 
to concatenate (cat) all the files (type f) which name ends with txt (case-insensitive: **i**name) in directories which are at maximum two levels deep, output to the file *all (>> *directs output to end of a file, single > empties the file first).
 
man locate or
man updatedb
 
should tell you how locate works
 
:D
 
Oh, sorry for additional stuff you didn't ask - I miss my Linux box and bash*.
 
*) default shell

---

### Post by bk452 on 2005-04-22
Thank you so much for the additional info.  I was really afraid of the command line but it grew on me.  I think it's the speed and the clear rundown of what's happening instead of giving me something pretty to look at but really doesn't tell me what's going on.

---

### Post by heimo on 2005-04-22
When I was beginning to learn shell (it never ends!) I would have been happy if someone had told me to read *man bash. *Well. Probably not happy. Probably annoyed. But I'd have been happy if I had read that manual page several years earlier.
Keyboard shortcuts. 
^L = clear screen, refresh screen (for example, some program outputs to the same screen while you're editing in full screen mode and messes your view, use this)
^K = kill end of the line
^A = go to the beginning of the line
^D = exit
^E = go to the end of the line
 
These are what come to my mind - there are more - and I use more, but at some point you stop thinking about it.
 
Also good thing to learn early is to use some editor that is widely available and works in text mode. It doesn't matter which editor it is (as long as it's vim ;) You can change it later: nano, pico, joe, emacs, vim, vi... Lots and lots of editors out there, but it makes life easier if you know at least one well.
 
I think I used pico at first and changed to vim later. I think two most common ones are emacs and vi (or vim).
 
I think it's not a requirement to know any of this to use Linux. But command line is extremely powerful tool, you can do just about anything in console. Surf web? lynx, links and wget
 
There are lots of tutorials about basic shell commands. Also lots of good books. The important thing - in my opinion - is to have fun while learning. Never get frustrated. There's always way to do it, but there's rarely one and only way to do it. It's a toolkit and the power lies in the creativity of the person in front of the keyboard. Combining commands, scripting - getting around if neccessary.
 
Heh. I think you know what I'm saying. We can only hope that more people could feel the thing.
 
I was reading very old Unix manual ( I think it was from early 70's) and I was laughing out loud as it was all very familiar to me. The same commands were there. The filesystem structure was familiar, too.
 
One thing you should learn early is jobs. You can put jobs in background (bg), bring them back to fereground (fg), list (jobs), kill, and so on. If you're running commands which must be executed in a sequence, you can enter multiple commands on one line - separate with semicolon ;
 
If you want to put a command on background (you know it'll take some time to finish), you can use & to do it. 
tar czvf file.tar.gz * &
(create compressed package of all files (except some special ones) in this directory - do it on the background. Now you don't need to wait for that command to finish. You can continue doing the other things you do. :)
 
I feel so tied up when I have to use MS-DOS command prompt. That's not a shell. That's a very sad joke. It's awful to use, it lacks power. People who defend MS-DOS prompt haven't ever learnt to use some real unixlike shell. (That's my honest opinion, if someone reading this argues against, please keep it to yourself, I'm not interested.)
 
Keep on hacking! :)
 
EDIT: Oh, here it is! I consider this the best resource for starting to learn unix shell! :) Yeah, it's 1971 and some things have changed, but it's basicly the same. Next resource is *man bash*
[http://cm.bell-labs.com/cm/cs/who/dmr/1stEdman.html]("http://cm.bell-labs.com/cm/cs/who/dmr/1stEdman.html")




EDIT: typos, syntax errors (I wish I could write better English)

---

### Post by bk452 on 2005-04-23
You've provided a wealth of info and I appreciate it.  Thanks.  I'm going to be busy looking up those references. Thanks for answering a newbie.

---

### Post by doclivingston on 2005-04-23
You have to be careful if some files have spaces in their name. The first time you make the mistake of using normal command with files that have a space in the name and lose something, you learn not to do it again. I'd rewrite 
```
for name in $(find -type f -max-depth 2 -iname '*txt'); 
  do cat $name >> all; 
done
```

to ```
find -type f -max-depth 2 -iname '*txt' -exec cat '{}' ';' >> all
```

the "-exec" bit says to run the following command replacing the '{}' with the file name. You use ';' to tell it that the command has finished. Alternatively have a look at the manpage for xargs (particularly things with the form `find XXX -print0 | xargs -0 YYY`)

[edit: fixing some grammer]

---

### Post by heimo on 2005-04-23
Thanks doclivingston! You're absolutely correct. I forgot that it's possible to have spaces in filenames... :D It's only technically possible on my systems... I was going to use exec flag in my example, but went with the for-loop, which I remembered easier. Definitely better to use exec.

The correct flag for max depth is -maxdepth (my mistake) and it's possible to escape semicolon with backslash \;

---

### Post by fordfan753 on 2005-04-23
Try Beagle, it indexes your files and allows you to search through them for just about anything, it is currently CVS...but worth a good look, don't bother if you have a slow computer, it takes up a lot of memory.

---

