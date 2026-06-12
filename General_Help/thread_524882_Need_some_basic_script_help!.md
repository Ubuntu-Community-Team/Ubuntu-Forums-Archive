---
title: "Need some basic script help!"
date: 2007-08-13
forum: General Help
---

### Post by Jolee on 2007-08-13
Hi everybody! (Doc. Nick ftw)

Im new to Linux and the Ubuntu 7.04 which I am using now, and I started learning some basic scripting using the linuxcommand.org guide. But I ran into some problems when I wrote the script as following:

[I]#!/bin/bash

#make_page - A script to produce an HTML file

cat <<- _EOF_
      <HTML>
      <HEAD>
                 <TITLE>
               My System Information
                 </TITLE>
      </HEAD>
      <BODY>
      <H1>  My System Information </H1>
      </BODY>
      </HTML>
_EOF_[/I]

_________

When I run it saying:
 make_page > *nameofpage.html*
It just gives me the message:
bash: /home/joakim/bin/make_page: Permission denied

The file is created, but with nothing in it, its just an empty .html file /cry.
I really hope someone has the answear to this.

---

### Post by ThrobbingBrain66 on 2007-08-13
1. Make sure you've made the script executable: right-click file, properties, permissions, allow executing file as program

2, Call it like this: ./make_page > nameofpage.html

I did the above and your script worked for me.

---

### Post by Jolee on 2007-08-13
Ahh! Thanks alot, allways good to know that you can find a helping hand so quickly ;).

---

### Post by OldManRiver on 2007-08-14
All,

I need help with correct syntax of "IF" statement:

EX:```
$ln_lst = /somefile
  if [ $ln == ' ']  && [$ln == $ln_lst]
     then continue
  else
     echo "$ln"
  fi
```
This blows so need correct combo for the "AND"!

OMR

---

### Post by psusi on 2007-08-14
Your logic is flawed.  It makes no sense to say if a = b AND a = c.  Either it is equal to a, or b... the only way it is equal to both is if b and c are the same.

---

### Post by OldManRiver on 2007-08-14
> **psusi said:**
> Your logic is flawed.  It makes no sense to say if a = b AND a = c.  Either it is equal to a, or b... the only way it is equal to both is if b and c are the same.

You're right I need an "OR".

Script is processing as follows:```
clear
n=0
echo \n"Finding the Magic Yellow Files"\n
ls_lin="ls /home/nyled/myfiles/m_yellow*.txt"
ls_lst="/home/nyled/myfiles/m_yellow_list.txt"
#sh eval $ls_lin > $ls_lst
$ls_lin > $ls_lst
cat $ls_lst |
while read ln
  do
  n=`expr $n + 1`
  if [$ln == ' ']  || [$ln == $ln_lst]
     then continue
  else
     echo "$ln"
  fi
done
```

Using "ls" to create file list. Error I'm getting concerns the '[]'s.  Once I get this right, will open file and process the lines, where the "echo" is.

Thanks!

OMR

---

### Post by psusi on 2007-08-15
Your problem is with the ==, it is just = or -eq.

---

