---
title: "Stump the Master ?!"
date: 2008-07-05
forum: General Help
---

### Post by kevdog on 2008-07-05
Ok I just read:
[http://www.deer-run.com/~hal/UnixCommandLineKungFu.pdf](http://www.deer-run.com/~hal/UnixCommandLineKungFu.pdf)

Very informative.

One syntax argument I cant seem to get right is scp files with spaces in the name.  This often is a problem with transfering files with cygwin users on windows where filenames often have spaces.  Any solution for this

---

### Post by theshadowwithanmp5n on 2008-07-05
i think if you throw some quotes in there it'll work
My Stuff In Windows could be "My Stuff In Windows"
that should work.

if not you could just rename the file and fill the spaces with underscores.

---

### Post by bodhi.zazen on 2008-07-05
> **kevdog said:**
> Ok I just read:
[http://www.deer-run.com/~hal/UnixCommandLineKungFu.pdf]("http://www.deer-run.com/%7Ehal/UnixCommandLineKungFu.pdf")

Very informative.

One syntax argument I cant seem to get right is scp files with spaces in the name.  This often is a problem with transfering files with cygwin users on windows where filenames often have spaces.  Any solution for this

Do quotes not work ?

scp "file name" user@server:/home/user

Works on the linux side (not sure about cygwin)

Also you can winscp :

[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

winscp is a gui tool . You do not need to install anything on Windows (thus it is portable) and works similar to putty (if you use keys, Winscp uses your putty keys).

---

### Post by kevdog on 2008-07-05
Im talking specifically about spaces in directory names as in relation to this part of the command line syntax:

user@server:/home/user

so something like

"john doe"@server:"/cygdrive/c/My Documents/..."

Those quotes dont seem to work.

---

### Post by bodhi.zazen on 2008-07-05
> **kevdog said:**
> Im talking specifically about spaces in directory names as in relation to this part of the command line syntax:

user@server:/home/user

so something like

"john doe"@server:"/cygdrive/c/My Documents/..."

Those quotes dont seem to work.

Not sure which set of quotes you are asking about, but try escaping the spaces with a \ in combination with single quotes :

'john\ doe'@'server:/cygdrive/c/My\ Documents/...'

Works for the directory (on linux), not sure about the user name. May be

'john doe'@'server:/cygdrive/c/My\ Documents/...'

---

