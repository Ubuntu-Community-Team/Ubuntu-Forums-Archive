---
title: "shell programing help"
date: 2013-09-04
forum: General Help
---

### Post by alex_11704 on 2013-09-04
help me to find out the problem


#!/bin/bash
$t = ""
echo "CLI Chat version 0.5 beta"
echo "Joining chat room..."
echo "" > /chat.txt
clear
echo "`whoami` at `tty` joined chat room" > who.txt
cat /chat.txt who.txt > chat.txt
cat chat.txt > /chat.txt
cat /chat.txt
echo "------------------------------------------------------------"
while [ 1 -eq 1 ] ; do
read chat
while [ $chat -eq $t ] ; do
clear
cat /chat.txt
echo "-------------------------------------------------------------"
read chat
done
echo $chat > 1.txt
clear
echo "From `whoami` at `tty`-" > who.txt
cat /chat.txt who.txt 1.txt > chat.txt
cat chat.txt > /chat.txt
cat /chat.txt
echo "-----------------------------------------------------------"
done

---

### Post by alex_11704 on 2013-09-04
pm me

---

### Post by Impavidus on 2013-09-04
First of all, remove the **$** in **$t=""**. This cannot work.

There are other things that aren't really good practice, like letting users write to the root directory and the way you copy lines.```

echo $chat > 1.txt
clear
echo "From `whoami` at `tty`-" > who.txt
cat /chat.txt who.txt 1.txt > chat.txt
cat chat.txt > /chat.txt
cat /chat.txt
echo "-----------------------------------------------------------"
```is equivalent to, but without creating the auxiliary files```

clear
echo From $(whoami) at $(tty)- >>/chat.txt
echo $chat >>/chat.txt
cat /chat.txt
echo -----------------------------------------------------------
```
>> instead of > appends to a file instead of creating a new one.

---

### Post by prodigy_ on 2013-09-04
**while [ 1 -eq 1 ]** is a bit ugly. Use **while true** instead.

**[ $chat -eq $t ]** requires both parts to be integers and is prone to breaking because of unquoted vars. I suppose **[ "$chat" == "$t" ]** is closer to what you want. But since **$t** is just an empty line the condition could be further simplified by dropping **$t** completely: **while [ -z "$chat" ]** would do.

---

