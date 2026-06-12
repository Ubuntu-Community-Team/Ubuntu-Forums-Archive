---
title: "help copying files"
date: 2007-05-16
forum: General Help
---

### Post by m.musashi on 2007-05-16
I have a bunch of pictures stored in multiple directories within a parent directory along with a bunch of html files. I would like to extract all the pictures and put them in one directory and leave behind all the html files. I tried
```
cp -r ~/website/*.jpg ~/pictures/
```
but it gives an error about no such file or dir. I think it doesn't like the wild card or it isn't digging into the sub dirs to find the files. Any help is appreciated.

Thanks.

---

### Post by Ziox on 2007-05-16
remove the "-r".  I think that looks for a directory.

---

### Post by m.musashi on 2007-05-16
Thanks. I tried with the -r but I got the same error
```
cp: cannot stat `/home/jim/website/*.jpg': No such file or directory
```
I think it doesn't like that there isn't a file matching that in the parent directory but I thought I should look into the subdirectories with the -r option. I guess not.

---

### Post by Ziox on 2007-05-16
I get that error when It can't find the any files matching the argument...

---

### Post by m.musashi on 2007-05-16
I put a file in the first dir with a .jpg extension and it worked fine but only for the parent directory. It is not looking in all the sub dirs. I thought the -r would do that but it isn't.

Any idea how do I get it to pull .jpg files from all the sub dirs?

---

### Post by m.musashi on 2007-05-16
FWIW, I found this
```
find <start directory> -iname "<all my files type>" -exec cp {} <target_dir> \;
```
It seemed to work. I guess just plain ol' "cp" is not what I needed.

---

### Post by Ziox on 2007-05-16
i don't get the "{ }" part of that command...could you explain it...

also, what's FWIW?

---

### Post by m.musashi on 2007-05-16
FWIW = for what it's worth. It's just lazy shorthand I picked up. Sorry.

I have no idea what the {} part or much else in that string means. I found it in some random forum. However, it seemed to work. Dumb luck I guess.

---

### Post by strabes on 2007-05-17
I'm not sure but you might have have to manually create the ~/pictures directory. I don't know if cp creates the destination directory or not.

---

### Post by m.musashi on 2007-05-17
No, it didn't create a directory. I had to make that first.

---

