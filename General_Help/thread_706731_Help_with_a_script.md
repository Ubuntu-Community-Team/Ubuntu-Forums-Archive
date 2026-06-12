---
title: "Help with a script"
date: 2008-02-24
forum: General Help
---

### Post by jmvidalvia on 2008-02-24
Hi!
I am trying to execute this script:
```
#!/bin/bash
DIR="/home/datos/fotos/"

for FILE in `find $DIR -iname *.jp* -type f -size +1000k -print0 | xargs -0`
do
        mogrify -resize 1280x960 "$FILE"
done
```

But it fails everytime it finds a sub-directory with blank spaces in its name.
Probably I am missing something...:oops:
Thanks a lot!

---

### Post by ghostdog74 on 2008-02-24
don't use for loop. Use a while loop and always double qoute your variables.
```

find ..... | while read -r FILE
do
  mogrify........
done

```
or
just simply
```

find $dir -name "*.jpg" -type f -size 1000k -print0  | xargs -0 mogrify -resize 1280x960

```

---

### Post by jmvidalvia on 2008-02-25
Thanks a lot!
I modified my script as follows, according to your suggestions:
```
#!/bin/bash
DIR="/home/datos/fotos"
find $DIR -iname "*.jp*" -type f -size +1000k -print0 | xargs -0 mogrify -resize 1280x960

```
It is running fine now. :)
Just one question: I don't understant why I can't use for for loops...?
Thanks!

---

### Post by Mr. C. on 2008-02-25
> **jmvidalvia said:**
> 
Just one question: I don't understant why I can't use for for loops...?

Evaluate the man page regarding for and while loops:

```

       for name [ in word ] ; do list ; done
              The list of words following in is expanded, generating a list of
              items.  The variable name is set to each element of this list in
              turn, and list is executed each time.  If the in word  is  omit-
              ted,  the  for  command  executes  list once for each positional
              parameter that is set (see PARAMETERS below).  The return status
              is  the  exit  status of the last command that executes.  If the
              expansion of the items following in results in an empty list, no
              commands are executed, and the return status is 0.

       while list; do list; done
              The while command continuously executes the do list as  long  as
              the  last  command  in list returns an exit status of zero.  The
              until command is identical to the while command, except that the
              test  is  negated;  the  do list is executed as long as the last
              command in list returns a non-zero exit status.  The exit status
              of  the  while and until commands is the exit status of the last
              do list command executed, or zero if none was executed.

```

a "word" is not the same as a "list".

MrC

---

