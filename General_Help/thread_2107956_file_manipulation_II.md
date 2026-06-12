---
title: "file manipulation II"
date: 2013-01-23
forum: General Help
---

### Post by Herbon on 2013-01-23
A few months ago I had accidentally moved the contents (mp3 files) out of their folders, up one layer in the main folder.

> find ./ -iname "*.avi" -exec mv '( )'  /home/SillyNubee/Music/Jazz

When I re-ran the command, I got a "Find: missing argument to 'exec'

Is there a more elegant way to move the contents into the main folder?!?! 

Finally

I have files (mp3) with weird names the start with numbers followed by the file name, how can I just delete the weird characters and leave name?

Thanks

---

### Post by steeldriver on 2013-01-23
Try

```
find . . . -exec mv -t /home/SillyNubee/Music/Jazz/ {} + 
```Also I believe it's better practice to use single quotes for 'find' arguments i.e. '*.avi' not "*.avi" - to stop any possibility that the shell expands them before they are passed to 'find'

---

### Post by Herbon on 2013-01-23
> **steeldriver said:**
> Try

```
find . . . -exec mv -t /home/SillyNubee/Music/Jazz/ {} + 
```Also I believe it's better practice to use single quotes for 'find' arguments i.e. '*.avi' not "*.avi" - to stop any possibility that the shell expands them before they are passed to 'find'

Great it worked!!

Any solution to the rename the files!?!

And how do you guys keep all these commands str8 in your heads :confused:

---

### Post by steeldriver on 2013-01-23
Sorry - missed the 2nd q

You can use the 'rename' command with a regular expression that defines the bit you want to replace, e.g. to remove 1 or more leading digits

```
$ rename -nv 's/^[0-9]+//' *.mp3
162832file.mp3 renamed as file.mp3

```(the '-n' is a dry-run, it won't actually do the rename until you remove that). You will need to be precise about exactly what "weird characters" you want to remove, and you'll want to decide how to handle any potential naming conflicts.

---

### Post by Herbon on 2013-01-23
> **steeldriver said:**
> Sorry - missed the 2nd q

You can use the 'rename' command with a regular expression that defines the bit you want to replace, e.g. to remove 1 or more leading digits

```
$ rename -nv 's/^[0-9]+//' *.mp3
162832file.mp3 renamed as file.mp3

```(the '-n' is a dry-run, it won't actually do the rename until you remove that). You will need to be precise about exactly what "weird characters" you want to remove, and you'll want to decide how to handle any potential naming conflicts.


I'm not clear on this

---

### Post by Vaphell on 2013-01-23
> And how do you guys keep all these commands str8 in your heads

once you know what they do, they are as simple as using words in everyday conversations ;-)


```
rename <expression> file(s)
```


s/from/to/ is substitution: pattern <from> is replaced by <to>

rename uses regular expressions
^[0-9]+ = at the beginning of the line (^) match 1+ (+) digits ([0-9])
and that matching part is replaced by empty string which is equivalent to removing it. Example shows that the leading numbers are indeed deleted.

-v is verbose mode so rename says what it does
-n doesnt actually perform the operation (dry run) so if you want to actually rename, you don't use that switch

---

### Post by Herbon on 2013-01-24
Cool Info!

Thanks!

---

