---
title: "Find files by file type - not file extension"
date: 2012-11-30
forum: General Help
---

### Post by lildigiman on 2012-11-30
I notice that in Nautilus on Ubuntu (specifically 10.10, but I'm sure it could still apply to 12.10) that there is a "Type" column when listing files in the list view. The string displayed there shows the file type of the respective extension. However, if no extension is given on the file it automagically knows what filetype it is and displays it.

For example if I have a file called "MyFlashVideo" (which is indeed a flash video), then the Type column will display "Flash video" automagically. If I rename if to "MyFlashVideo.txt" it corrects itself incorrectly and calls it a "plain text document".

Anyway, my question is how I can search my file-system for files without any extensions by their file type. (In a specific example suppose I want to find all the flash videos that don't have extensions on my computer)

Any help is greatly appreciated!

---

### Post by PinkFloyd102489 on 2012-11-30
Dunno how to do it in the GUI but on the command line you can use the *file* command with the --mime-type switch.

```
man file
```

---

### Post by picaflor on 2012-11-30
Hi,

I've never tried it, but this:

[http://linux.die.net/man/1/file](http://linux.die.net/man/1/file)

looks like it might work.

Good Luck,

Anne

---

### Post by Vaphell on 2012-11-30
```
find -type f -iregex '^.+/[^./]+$' -exec file '{}' \; | grep -i 'flash video'
```
it's recursive and takes a while, so test it in some location with few files first.

---

### Post by lildigiman on 2012-12-01
Hey all, thanks for the responses, and thank you Vaphell, your script works well, however searching with grep for something specific as "Flash video" does not work. After looking at what gets dumped without grepping for anything in specific I see that "MPEG" fits the bill for what I'm looking for, as well as "AVI" etc...

Awesome!

---

