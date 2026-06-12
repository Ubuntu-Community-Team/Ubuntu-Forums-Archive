---
title: "Command chaining / piping"
date: 2007-07-29
forum: General Help
---

### Post by sefs on 2007-07-29
Hi i am trying to delete a number of directories in a main directory.

I can use the find command to find all the directories i want to delete like so...

find ~/Desktop/joomlasvn -name '.svn' -type d

but now i want to delete them in one go .... how do i set up the chaing of

rm -rf and find ~/Desktop/joomlasvn -name '.svn' -type d > rm -rf

Thanks.

I tried find ~/Desktop/joomlasvn -name '.svn' -type d -delete
but it tells me the dirs are not empty.

---

### Post by Wim Sturkenboom on 2007-07-29
The find command has an exec option that you can use to execute a command on the files it has found.

As an example
```
 find . -name "*.txt" -exec grep "mytext" {} \;
```

In your situation probably ([COLOR="Red"]I don't take responsibility for this :) if it does something unexpected[/COLOR])
```
find . -name ".svn" -type d **-exec rm -rf {} \;**
```

Please note that the backslash and the semicolon are part of the command.

---

### Post by dagnabit dang doohickey on 2007-07-29
```
find ~/Desktop/joomlasvn -name '.svn' -type d -exec rm -r {} +
```

---

