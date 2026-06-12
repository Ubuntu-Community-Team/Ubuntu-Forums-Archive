---
title: "RAR Archiver"
date: 2007-02-16
forum: General Help
---

### Post by ZipCrash on 2007-02-16
Question about the built in Archiver. Is there any way to change the compression settings. It's attempting to compress my files too much and takes for ever. When I was using Windows and used WinRAR you could select the option and I'd just do store because compressing a few extra MB isn't worth the long wait. Does anybody know if I can change that, if not is there a better program out there? Thanks.

---

### Post by yabbadabbadont on 2007-02-16
zip -0 archivetobecreated.zip filestostorewithoutcompression

---

### Post by ZipCrash on 2007-02-16
What if I want rar instead of zip? Do I just change to rar and change the extension to .rar or??? And is there no way to do it through gui without having to type that command in the terminal every time?

---

### Post by yabbadabbadont on 2007-02-16
Sorry, no clue.  I don't use gnome or the gui archiver.  If you are not going to be compressing the files you archive, what difference does it make which archive format you use to store the uncompressed files?

---

### Post by ZipCrash on 2007-02-17
Yea I guess it doesn't, just what I'm use to using. I'm surprised at the lack of options on the archiver, atleast gui wise.

---

### Post by anaconda on 2007-02-17
You can also use winrar in  ubuntu. Through wine. WinRAR works just fine..

---

### Post by Muzik83 on 2007-02-17
doing a rar --help reveals the following:
...
  m<0..5>       Set compression level (0-store...3-default...5-maximal)
...

Have you tried m0 on the command line?

-sean

---

### Post by ZipCrash on 2007-02-17
Yea I'm just trying to find a program that intergrates into gnome like WinRAR does in Windows. Don't want to have to use command lines all the time...seems like the exact opossite of the whole point of Ubuntu.

---

