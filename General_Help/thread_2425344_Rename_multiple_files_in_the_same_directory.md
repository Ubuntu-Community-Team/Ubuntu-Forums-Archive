---
title: "Rename multiple files in the same directory"
date: 2019-08-24
forum: General Help
---

### Post by tech291083 on 2019-08-24
Hi All,


To rename a bunch of files in a particular folder, I normally open terminal in that folder and run the following command, which is basically an example of all jpeg files being renamed to what I like. And they are renamed memory 1.png, memory 2.png and so on.


```

ls | cat -n | while read n f; do mv "$f" "memory $n.png"; done

```



But now I want to bulk rename files in a folder in such a manner that the new filenames begin with a number of my choice and it gets increased by 1 each time, just like a loop in any programming language. I am not good at all at bash scripting, awk, sed etc.


If I want to rename all png files in a folder with the 1st one being memory 54.png and the next one being, memory 55.png and so on.


How can I do so?


Thanks.

---

### Post by TheFu on 2019-08-24
```
for N in {1..24} ; do 
   echo "# $N  "; 
done
```
and

```
for filename in "$@"; do
   echo $filename
done
```

To use $@, you just pass in a pattern to the script. Filenames can't have spaces or "funny" characters that would be interpreted by bash.  Spaces cause all sorts of issues for scripting.  Just.Don't.  It isn't worth it.  Most punctuation and any <shift>-number characters are generally a problem.

There is a small perl tool, called **rename**. I use this for bulk renaming a few times a day. It uses perl RegEx patterns, which are extremely flexible, but I don't know how to have it add sequential numbering.  I use it mainly for photo organization, so photos are always in order for a specific event.  The actual numbers aren't important, so the numbers that my camera creates are fine, but I want descriptive filenames for each photo too.
```
140-Kumar-Use_Me.jpg
141.jpg
142.jpg
143-Goats.jpg
144.jpg
145-World_Peace_Pagoda-best.jpg
146-World_Peace_Pagoda.jpg
147-World_Peace_Pagoda.jpg
```
Images help us to remember the event more fully 10+ yrs later.  Filenames without descriptions aren't good enough to warrant the effort, but still fill in details of the experience. [https://en.wikipedia.org/wiki/Shanti_Stupa,_Pokhara](https://en.wikipedia.org/wiki/Shanti_Stupa,_Pokhara) is the approximate location for those photos.  They are also GPS location tagged.  Notice how the names don't have spaces?

More about **rename** [https://www.tecmint.com/rename-multiple-files-in-linux/](https://www.tecmint.com/rename-multiple-files-in-linux/)

Does that help with some ideas?

Please:
* don't use ls to feed in filenames (many reasons this is NOT a good solution) ; use "globbing" for matching filenames
* don't use cat ;  pretty much ever (there are exceptions, but those happen about once every 6+ yrs).  It isn't needed. Just wastes an extra process and pipes

---

### Post by freedombacon on 2019-08-24
Alternatively and if you can use a GUI, KDE's file manager Dolphin can do exactly this.

---

### Post by dragonfly41 on 2019-08-24
Also pyrenamer in software repo.

---

### Post by cruzer001 on 2019-08-24
[https://packages.ubuntu.com/bionic/dolphin](https://packages.ubuntu.com/bionic/dolphin)
I would not like bringing in all of those depends just to bulk rename.

My most favored bulk renamer "Pyrenamer" has been dropped from our software sources.

So as a quick fix (needed something right then) I did download Thundra file manager. At least that will not pull in those Qt packages.  Still I do not agree with having to download any file manager for such a small task and will find a pyrename replacement one day.

---

### Post by dragonfly41 on 2019-08-24
> [COLOR=#000000]My most favored bulk renamer "Pyrenamer" has been dropped from our software sources.[/COLOR]

It is in 16.04 repo. I have just installed it.

---

### Post by cruzer001 on 2019-08-24
Dropped in 18.04 :(

---

### Post by The Cog on 2019-08-24
```
n=55 ; for f in folder/*png ; do echo mv "$f" "folder/memory-$n.png" ; n=$(($n+1)) ; done
```
If this prints the commands you want, remove the "echo" so it does the commands rather than just printing them.
As TheFu says: Don't do spaces. It'll end in tears.

As an afterthought, if you cd into the folder you don't need it in the command:
```
n=55 ; for f in *png ; do echo mv "$f" "memory-$n.png" ; n=$(($n+1)) ; done
```

---

### Post by dragonfly41 on 2019-08-24
Re: Pyrenamer .. can the 16.04 deb file be installed on 18.04 via GDebi Package Installer?


[https://pkgs.org/download/pyrenamer](https://pkgs.org/download/pyrenamer)

---

### Post by cruzer001 on 2019-08-24
So I went to pkgs.org and downloaded the universal.deb package for Pyrenamer.  It installed on 18.04 and though not thoroughly tested it does work.  

I have my favorite renamer back :)

ps
gdebi unnecessary

---

