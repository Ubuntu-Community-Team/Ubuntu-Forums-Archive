---
title: "Display a directory tree"
date: 2014-04-06
forum: General Help
---

### Post by soul2 on 2014-04-06
Hi, I need to make a directory tree which display the full path of the directory whose tree is being created...looks like this :

```

`---Folder1
|      `---text1.txt
|      `---text2.txt
`---Folder2
|      `---subfolder1
|      |      `---text3.txt
|      `---subfolder2
|      |      `---subfolder3
|      |      |      `---text4.txt
|      |      `---subfolder4
|      |      |      `---text5.txt
|      `---subfolder5
|      |      `---text6.txt
`---text7.txt
`---text8.txt

```

Is there anyway to do this without using the sed or awk feature ?
Thank you.

---

### Post by steeldriver on 2014-04-06
There's a nice program for that called... 'tree' ;)

IIRC it's not installed by default, but you can install from your favorite package manager, or from the command line

```
sudo apt-get install tree
```

---

### Post by soul2 on 2014-04-06
Thanks for the reply!
But I actually need to do this on a bash shell...

---

### Post by freebird54 on 2014-04-06
> **soul2 said:**
> Thanks for the reply!
But I actually need to do this on a bash shell...

That's where it works - I don't yet know if it will follow links somehow though.....

OK - it will - use ```

tree -lshn
```
for a list with follow links on, sizes, human readable as an example.  Lets you turn color on and off, ASCII or graphic chars, set max level to go down... etc etc

---

### Post by soul2 on 2014-04-11
Hi,
 I am writing a bash shell script that display the contents of a directory in the form of a tree structure. The output of the directory is suppose to be like this when I type in the command "./Script1.sh subdirectory" in the main Directory:

```

`---Folder1
|      `---text1.txt
|      `---text2.txt
`---Folder2
|      `---subfolder1
|      |      `---text3.txt
|      `---subfolder2
|      |      `---subfolder3
|      |      |      `---text4.txt
|      |      `---subfolder4
|      |      |      `---text5.txt
|      `---subfolder5
|      |      `---text6.txt
`---text7.txt
`---text8.txt
```

However, my final output is like this:
```

`---Folder1
`---Folder2
`---text7.txt
`---text8.txt

```

What happen ? why it  is not showing the full path of the directory ?
and when I try to move the script into the sub directory and test it again, it does showing what I am expecting to see

Please help...

---

### Post by sisco311 on 2014-04-11
Please don't start multiple threads on the same topic. Threads merged.

---

### Post by sisco311 on 2014-04-11
Could you post the script?

---

### Post by soul2 on 2014-04-11
> **sisco311 said:**
> Could you post the script?

This is the one that goes worong...
```

#!/bin/bash
#echo $(ls -a $1)


param=2
tab=0
zero=0
if [ $# -ge $param ]
then
  tab=$2
fi




for i in $(ls -a $1)
do
  if [[ $i != "." && $i != ".." ]]
  then
    directory=$1
    directory+=$i
    directory+="/"


    j=0


    while [ "$j" -lt "$tab" ]
    do
      echo -ne "|\t"
      ((j++))
    done


    echo -ne "\`---"
    echo $i
    if [ -d "$directory" ]
    then
      #echo -ne ""
    #  echo $directory
      sp=$tab
      ((sp++))
      ./$0 $directory $sp


    fi
  fi




done


```

---

