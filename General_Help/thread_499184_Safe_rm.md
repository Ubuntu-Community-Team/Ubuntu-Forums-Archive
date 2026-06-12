---
title: "Safe rm"
date: 2007-07-12
forum: General Help
---

### Post by olejorgen on 2007-07-12
Today I almost burned myself quite bad with rm. I did
```

gzip <file>
// ...
rm <file>.gz

```
woops, turns out gzip removed <file>

Luckily it was not an important file, but it could easily been.

So, I want a alternative rm command that moves the file to a hidden directory on the current partition. (must handle dublicate filenames) If it's an rm-alias it should probably only work when a certain enviroment variable or maybe the bash -i flag is set.

A simple alias rm='mv <something>' wont do, since mv moves directories too

I could ofcourse make a simple bash script, but my sh is not perfect and I'm pretty sure this have been done a dozen times before.

PS: the search restriction on 3 or more letters is redicolous (esp. when searching for title only. unix commands are short)

---

### Post by zvacet on 2007-07-12
**rm** does not move files it delete them.To move files use **mv** command or **cp** (copy).If you decide to use cp when you done it you can delete file from the place you copyed it from.

---

### Post by olejorgen on 2007-07-12
uh, I am fully aware of this.

I can understand that some people feel that this is uneccessary. If you use rm, be sure (or something) But I think even when you are very careful, misstakes can happen (*), and I think we all agree that it sucks too lose data.

(*) Like my examle. I was "sure" that gzip would not remve the file.
(*) I, know we all do backups, but not by the minute

I'm not in any way saying that this behavior should replace rm, I'm just asking for and alternate rm with this behavior. (It is my "god" given right to alias whatever I want)

---

### Post by jyba on 2007-07-12
I suppose everyone accidentally 'rm's something important at some stage. I see it as a rite of passage; you do it once, it's burned into your brain, and you never do it again.

You could of course alias 'rm' to 'rm -i', but if you tend to use 'rm' without having your brain in gear then you will probably use 'rm -i' without thinking too.

Here is the link to a script that does most of what you want...
[http://blog.ibao.net/linux/2004/02/27/safe-rm/](http://blog.ibao.net/linux/2004/02/27/safe-rm/)

If you want it to check for duplicate filenames you could adapt it like this...

```
#!/bin/bash
#
#  A tiny script that moves files to a wastebasket, rather than deleting them
#+ (and doesn't overwrite previously deleted files of the same name).

[ -d ~/.deleted ]
if [ $? -eq 1 ]; then
    echo "Creating directory."
    mkdir ~/.deleted;
fi

random_suffix=$RANDOM

for file in $@; do
    if [[ -e ~/.deleted/$file ]]; then
        mv $file ~/.deleted/${file}.${random_suffix}
    else mv $file ~/.deleted/
    fi
done
```

---

