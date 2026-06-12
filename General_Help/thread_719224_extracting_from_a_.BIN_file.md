---
title: "extracting from a .BIN file"
date: 2008-03-08
forum: General Help
---

### Post by skydiver|goose on 2008-03-08
I tried the threads that come up when I search "extracting .bin archives", but they didn't work for me. I have a .bin file with all my skydiving videos archived inside of it; but I can't figure out for the life of me how to extract them.

---

### Post by taurus on 2008-03-08
Try something like

Applications -> Accessories -> Terminal
```
chmod 755 *filename.bin*
./*filename.bin*
```

---

### Post by skydiver|goose on 2008-03-08
goose@goose-laptop:~/Desktop$ chmod 755 SkyVid.bin
goose@goose-laptop:~/Desktop$ ./SkyVid.bin
bash: ./SkyVid.bin: cannot execute binary file
goose@goose-laptop:~/Desktop$ 


It's not an executable, it's an archive. but I don't have a .cue file

---

### Post by sarukun1228 on 2008-03-09
You can try in Terminal, 

$unzip FILENAME.bin

I tried it on a bin file, but it did not work, but I don't know if the file is even an archive.

---

### Post by lha on 2008-03-09
> **skydiver|goose said:**
> I tried the threads that come up when I search "extracting .bin archives", but they didn't work for me. I have a .bin file with all my skydiving videos archived inside of it; but I can't figure out for the life of me how to extract them.

Check [http://wiki.linuxquestions.org/wiki/CD_Image_Conversion]("http://wiki.linuxquestions.org/wiki/CD_Image_Conversion"). There's a link to the source code of bin2iso, a program that should be able to convert .bin files to .isos. (Iso files can be mounted.) Bin2iso doesn't seem to be in the repos, so you'll have to compile it.

---

