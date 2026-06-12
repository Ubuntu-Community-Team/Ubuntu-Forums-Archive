---
title: "send 10 random images with mutt?"
date: 2012-10-15
forum: General Help
---

### Post by sohlinux on 2012-10-15
I can send a random image as an attachment to an email address using mutt but how can I send 10 random images from a folder and attach them all and email them?

the following works fine with one random image

mutt -s "10 random images" [email]my@email.com[/email] -a "$( find /home/images -type f | sort -R | head -1 )" < message.txt


thanks

---

### Post by Vaphell on 2012-10-15
try this
```
while read f; do files+=( "$f" ); done < <( find /home/images -type f | sort -R | head -10 )
mutt -s "10 random images" -a "${files[@]}" -- my@email.com < message.txt
```

---

### Post by sohlinux on 2012-10-15
> **Vaphell said:**
> try this
```
while read f; do files+=( "$f" ); done < <( find /home/images -type f | sort -R | head -10 )
mutt -s "10 random images" -a "${files[@]}" -- my@email.com < message.txt
```

:(
-bash: syntax error near unexpected token `mutt'

---

### Post by sohlinux on 2012-10-15
also it must only choose  jpg type -iname '*.jpg' ?

while read f; do files+=( "$f" ); done < <( find -iname '*.jpg' /home/images -type f | sort -R | head -10 )
mutt -s "10 random images" -a "${files[@]}" -- [email]my@email.com[/email] < message.txt

now just hangs >

---

### Post by Vaphell on 2012-10-15
when using find always put the directory first and the criteria second

how do you run it?
```
files=()
while read f; do files+=( "$f" ); done < <( find /home/images -iname '*.jpg' -type f | sort -R | head -10 )
mutt -s "10 random images" -a "${files[@]}" -- my@email.com < message.txt
```
i added files=() because i don't know how you run it. If the code is wrapped in a script the array would be empty each time script is executed, so the line is not necessary. On the other hand if you redo the commands in the terminal, the file list would get bigger and bigger (+= adds new elements), never throwing previous values away.

---

