---
title: "&quot;For each file&quot; bash command"
date: 2008-07-09
forum: General Help
---

### Post by sblanzio on 2008-07-09
Hello!

I thought this should be an easy task, but instead it seems to be an enormous obstacle to overcome.

My problem is I have to enter a single bash command for each file descripted by a "path/wildcard" entry.

Example:

I wish to entry:

```

./myscript.sh ./dir/*.jpg

```

and to have performed this command:
```

images2mpg -M /usr/bin/ -d 5 -o SingleFileFound.mpg -i SingleFileFound.jpg

```
This one for every JPG file, just like the wildcard descripts. 
I don't care very much at the output file name.. it even could be "SingleFileFound.jpg.mpg" if this is easier to obtain.

(this command is used to convert a JPG in a MPG 5 seconds long)

I tried several ways but I'm a beginner in bash script and so I've looked around, even [in this forum]("http://ubuntuforums.org/showthread.php?t=508784") but everything I found does not work properly, expecially about managing spaces in file names.

Does anybody know a way to make this task work in shell? Is this possible?

thank you very much!!!
:)```

```

---

### Post by jamesapnic on 2008-07-09
Try something like this in your bash script

> for i in `find ./dir -name \*.jpg`; do
  NAME=`echo $i | sed -e 's/\.jpg//g'
  echo "doing $NAME"
  images2mpg -M /usr/bin/ -d 5 -o $NAME.mpg -i $NAME.jpg
done


---

### Post by ghostdog74 on 2008-07-09
using a for loop with find command makes you susceptible to error if file names contains spaces. use while loop and read instead. Also, in Bash, you can do simple substitution without calling external tools.
```

find . -name "*.jpg" -printf "%f:%h\n" | while IFS=":" read NAME PATH
do
 NAME=${NAME/.jpg/}
 images2mpg -M /usr/bin/ -d 5 -o "$PATH/${NAME}.mpg" -i "${PATH}/${NAME}.jpg"
done

```

---

### Post by sblanzio on 2008-07-10
Thank you everybody!

With your help I've almost done that.

I unluckily seems to have still some problems. Here is my script code:

```

#!/bin/bash

find . -name "$1" -printf "%f:%h\n" | while IFS=":" read NAME PATH
do
 NAME=${NAME/.jpg/}
 /usr/bin/images2mpg -M /usr/bin/ -I /usr/bin -d 5 -o "$PATH/${NAME}.mpg" -i "${PATH}/${NAME}.jpg"
 echo "$PATH/${NAME}.mpg" -- "${PATH}/${NAME}.jpg"
done

```
I added $1 in the "find" row to pass arbitrary file position

Now, when I execute that, let's say, this way:

./script.sh /imgs/*.jpg

The images2mpg command is correctly started but it doesn't seem able to work because it can't reach any other commands.
I get a lots of error messages like:
line 899 - "cat" command not found
or
line 146 - "rm" command not found
I don't remember exactly which commands it doesn't find but they seem to be "regular" shell commands, which should be found in /usr/bin. So i guess this is something related with the $PATH variable.

I tried to substitute the "PATH" variable like it was a user variabile, calling that "TEST" but this didn't work because I think the $PATH use is necessary to make this script work...

So, anybody has any idea how to solve this problem?

Also, forgive me if I ask more, how could I change this script to make it compatible with other formats different from .jpg? (obviously images2mpg already supports them)

THank you very much again for your help!

sincerely

---

### Post by ghostdog74 on 2008-07-10
why don't you just pass the path into the script without the *.jpg.  
```

./myscript /path 

```
makes things easier.
```


find "$1" -name ".jpg" -printf "%f:%h\n" | while IFS=":" read NAME PATH
do
 NAME=${NAME/.jpg/}
 /usr/bin/images2mpg -M /usr/bin/ -I /usr/bin -d 5 -o "$PATH/${NAME}.mpg" -i "${PATH}/${NAME}.jpg"
 echo "$PATH/${NAME}.mpg" -- "${PATH}/${NAME}.jpg"
done

```

---

### Post by sblanzio on 2008-07-10
> **ghostdog74 said:**
> why don't you just pass the path into the script without the *.jpg.  
```

./myscript /path 

```
makes things easier.


I could but I even need to load other formats of file (ex: tga, bmp). They are supported by images2mpg and so I'd like to load them too.

I think it should be more useful if I can specify my target using wildcards.

However, i must say that using the script you suggested in your last post and sending that command I get no output at all. Maybe there's something wrong in what i did.

I must say again I am very surprised it is such a pain to build a bash script that repeat one command for any file selected by wildcards. I think this kind of task should be possible through a command embedded within the linux shell...

Or maybe, as sometimes I guess, there's a better way to do this job and I haven't found that yet.

However, thank you very much for your help!

Any idea how to solve this problem is appreciated!

---

### Post by sblanzio on 2008-07-10
:)

re-editing my code together with your hints, I finally got something that does the job. At least for the present directory.

I had to substitute the PATH variable with another called DIR. I think it didn't work because it was confused with the enviromental variable $PATH.
I even introduced a TYPE variable to control the $1 input. (maybe $1 was enough?)



This is what I have got to work

```

#!/bin/bash

TYPE=$1

find . -name "*.$TYPE" -printf "%f:%h\n" | while IFS=":" read NAME DIR
do
NAME=${NAME/.$TYPE/}
 /usr/bin/images2mpg -M /usr/bin/ -I /usr/bin -d 5 -o "$DIR/${NAME}.mpg" -i "${DIR}/${NAME}.$TYPE"
 echo "$DIR/${NAME}"
done

```

This way when i type:
```

./script.sh jpg

```

This script processes every .jpg file in the present directory.

If instead I want all .tga to be processed, I just have to follow the script call with "tga" instead of "jpg".

Even if this is not perfect and maybe works only in the present directory, I am satisfied with this task now.

Thank you very much everybody! I appreciated your help!

If anybody would improve this script, please let us know!

sincerely

---

### Post by sblanzio on 2008-07-10
Uhmmm i think there's something wrong in the script.

It's recursive and if I wouldn't have noticed that it would have filled my hd.... please be careful.
:(

---

### Post by ghostdog74 on 2008-07-10
```

#!/bin/bash
string=$(echo $@ | awk '{gsub(" ", "|")}1')
eval find . -regextype posix-extended -regex "\"./.*(${string})$\""   | while read NAME
do
 echo "FILENAME : "$NAME
 PATH=${NAME%/*}
 NAME=${NAME##.*/} 
 echo "FILENAME PATH : " $PATH  
 echo "You do the rest"   
done

```

---

### Post by sblanzio on 2008-07-11
This one seems to work just perfectly!! :)

thank you very much

---

### Post by schmick on 2009-09-28
> **sblanzio said:**
> Hello!

I thought this should be an easy task, but instead it seems to be an enormous obstacle to overcome.

My problem is I have to enter a single bash command for each file descripted by a "path/wildcard" entry.

Example:

I wish to entry:

```

./myscript.sh ./dir/*.jpg

```

and to have performed this command:
```

images2mpg -M /usr/bin/ -d 5 -o SingleFileFound.mpg -i SingleFileFound.jpg

```
This one for every JPG file, just like the wildcard descripts. 
I don't care very much at the output file name.. it even could be "SingleFileFound.jpg.mpg" if this is easier to obtain.

(this command is used to convert a JPG in a MPG 5 seconds long)

I tried several ways but I'm a beginner in bash script and so I've looked around, even [in this forum]("http://ubuntuforums.org/showthread.php?t=508784") but everything I found does not work properly, expecially about managing spaces in file names.

Does anybody know a way to make this task work in shell? Is this possible?

thank you very much!!!
:)```

```
what about the old
for n in /path/*.jpg
do
  echo $n
  .....
done

let the system do the wildcard expansion

---

