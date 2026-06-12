---
title: "Rename files with mv or any other command in terminal starting with -.text.extension?"
date: 2014-11-21
forum: General Help
---

### Post by kim-stude on 2014-11-21
So like the title says how to: Rename files with '**mv**' or any other command in terminal that starts with **-.text.extension** ?

I allready know how to rename example: text.extension and hidden files but when it starts with **-.text** then I can't figure it out how.
I've been strugling with this quite a while because I can't find any information on google about this matter.

Point is I'm making a script that automate's renaming a file which starts with: **-.text.extension** but terminal thinks and knows ' **-** ' it's a command that cannot be renamed.  

This is actualy my first time ever when needed any assistance from anyone with scripting, I have allways found my self an answer to my question's in forum's or google but not now. :p


Thank you for understanding and I love to hear your answers about this soon! :p ):P

Using: (HP Compaq 6715b, Xubuntu 14.04.1 LTS.)

---

### Post by sisco311 on 2014-11-21
Check out BashPitfalls 3 (link in my sig). ;)

---

### Post by Vaphell on 2014-11-21
use -- (2x '-') to explicitly end the switch section of parameters. Everything after that should be considered a file.

```
mv -- -.text.extension whatever
```

or go with ./-.text.... that ./ prefix indicating current dir should disarm that boobytrap.

---

### Post by The Cog on 2014-11-21
There is also a rename command that might be easier to use.
> man rename

---

### Post by Vaphell on 2014-11-21
*rename* will also be affected by the "-something filename treated as an option param" problem and the solution is going to be the same, -- or ./

```
$ rename -n 's/abc/def/' '-.abc.txt'
Unknown option: .
Unknown option: a
Unknown option: b
Unknown option: c
Unknown option: .
Unknown option: t
Unknown option: x
Unknown option: t
Usage: rename [-v] [-n] [-f] perlexpr [filenames]
$ rename -n 's/abc/def/' -- '-.abc.txt'
-.abc.txt renamed as -.def.txt
```

---

### Post by kim-stude on 2014-11-25
> **Vaphell said:**
> use -- (2x '-') to explicitly end the switch section of parameters. Everything after that should be considered a file.



or go with ./-.text.... that ./ prefix indicating current dir should disarm that boobytrap.

Ok thank you Vaphell! "mv -- -.text.extension whatever" worked for me :D. 

This was also the easiest and fastest solution... The reason I stubled into this problem was that "yle-dl" downloads subtitles in that format "-.text.srt" and "Vlc or mplayer" can't load the subtitles automaticly if they ain't 
named with the same name as videofile.

---

