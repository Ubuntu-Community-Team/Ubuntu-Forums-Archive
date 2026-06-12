---
title: "send multiple files by email with mutt?"
date: 2013-10-03
forum: General Help
---

### Post by sohlinux on 2013-10-03
Hello,

I want to send 20 files 01.txt to 20.txt by email from the command line using mutt

the following works fine for 1 file
mutt  -s "1 file" [email]me@gmail.com[/email] -a /home/john/Documents/1.txt < mailmessage.txt 

the following works fine for all files in the folder
mutt  -s "all files" [email]me@gmail.com[/email] -a /home/john/Documents/*.txt < mailmessage.txt

but how can I just send 01.txt to 20.txt ?

thanks

---

### Post by SeijiSensei on 2013-10-03
If you want just to select files with the pattern [number][number].txt, you can use

```
mutt -s "all files" me@gmail.com -a /home/john/Documents/[0-9][0-9].txt < mailmessage.txt
```

---

### Post by sohlinux on 2013-10-03
> **SeijiSensei said:**
> If you want just to select files with the pattern [number][number].txt, you can use

```
mutt -s "all files" me@gmail.com -a /home/john/Documents/[0-9][0-9].txt < mailmessage.txt
```

thanks :)

---

### Post by Vaphell on 2013-10-03
{01..20} is better because it wont include 99.

---

### Post by sohlinux on 2013-10-03
thanks guys

I would like to take this a step further so I can attach files using find. so it will recurse through the specified folder and attach all .doc files, something like the following which didnt work for me..

mutt -s "recursive doc file" [email]me@gmail.com[/email] -a find -type f -name /home/john/Documents/*.doc < mailmessage.txt

---

### Post by Vaphell on 2013-10-03
```
shopt -s globstar
mutt -s "recursive doc file" me@gmail.com -a ~/Documents/**/*.doc < mailmessage.txt 
```
or
```
docs=()
while read -rd $'\0' f; do docs+=( "$f" ); done < <( find ~/Documents -iname '*.doc' -print0 )
mutt -s "recursive doc file" me@gmail.com -a "${docs[@]}" < mailmessage.txt
```

---

### Post by sohlinux on 2013-10-04
perfect, thanks :)

---

