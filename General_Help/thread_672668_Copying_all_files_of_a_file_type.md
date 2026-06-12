---
title: "Copying all files of a file type"
date: 2008-01-19
forum: General Help
---

### Post by Stoodle on 2008-01-19
I was wondering how I could copy all of the files of a file type within a directory. In this case, I want to copy all of the music files from my Stepmania folder to another folder.

On a side note, how do I mount usb hard drives. It showed up when I did lsusb on usb 004 but I didn't know what to do to mount it. Thanks.

---

### Post by odinfromvalhalla on 2008-01-19
You can copy all files of a file type like this:

1. open nautilus and go to the folder from were you want to copy the files.
2. select to View as List instead of View as Icons which is the default setting
3. arrange items by type.
4. now you can easily select all the items and copy them.

you could do another thing:
open a terminal and use the cp command: cp *.<your_file_type> <destination>

---

### Post by Stoodle on 2008-01-19
Well, the thing is, I wanted to go to a directory named Songs. In Songs, is over 2000 directories, each with a song. I wanted to have it just search within each folder and pull out the .mp3.
I'd really like to do this in terminal because on stuff like this, it's usually faster. I also want to become better at using it.
When I tried the terminal thing, this is what I got.
```

cp: cannot stat `*.mp3': No such file or directory

```

---

### Post by noynac on 2008-01-19
I use the find command to copy files from a directory and its subdirectories. An example is:

find /media/canon -name *.jpg -type f -exec cp \{} /home/modred/photos \;

Credit goes to:

[http://mail.python.org/pipermail/tutor/2006-July/047904.html](http://mail.python.org/pipermail/tutor/2006-July/047904.html)

---

### Post by Stoodle on 2008-01-20
Great help! =D
Only thing is, could you explain what each part of the line is?

---

### Post by nick_h on 2008-01-20
This should really have some quotes around the *.jpg
```
find /source/path -name '*.jpg' -type f -exec cp '{}' /destination/path \;
```

---

### Post by nick_h on 2008-01-20
> Only thing is, could you explain what each part of the line is?
Just saw your post :)

-name selects filenames matching a pattern

-type selects files of a certain type (f = normal file)

-exec executes a command for each matching file
in the command the '{}' is substituted with each match

For further details and examples see:
```
man find
```

---

### Post by Stoodle on 2008-01-20
I did that but this is what I got ```
/media/ILOVEYOU/Songs '*.mp3' -type f -exec cp '{}' /media/ILOVEYOU/iPod\ music/;
find: missing argument to `-exec'

```

---

### Post by nick_h on 2008-01-20
Did you escape the final ";" with a "\" ?

---

### Post by Stoodle on 2008-01-20
Almost worked! However, it was copying everything and not just mp3s.

---

### Post by nick_h on 2008-01-20
I think you might have missed the -name as well.
```
find /media/ILOVEYOU/Songs -name '*.mp3' -type f -exec cp '{}' /media/ILOVEYOU/iPod\ music/ \;
```

---

### Post by Stoodle on 2008-01-20
It's times like this where Linux becomes the sexiest thing ever made on a computer.

By the way, it means it worked!!!

---

### Post by noynac on 2008-01-20
Posting deleted. I missed second page of thread.

---

