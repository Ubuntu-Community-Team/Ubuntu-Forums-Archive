---
title: "cannot access partition d from ubnutu"
date: 2008-05-06
forum: General Help
---

### Post by Meydanb on 2008-05-06
hey everyone.
so i finally decided to say good bye to windows and tried out Linux, so i downloaded Ubuntu and installed it together with windows, i did not format, just installed it as is, but on a different partition from which the windows is installed on.

now. i started it and played around, and i noticed that in Places-->computer i do not see my other partition D: on which ubuntu is installed on.
i just have 15.7 GB Media my CD-Roms, floppy and "FileSystem".
i cannot access from anywhere in ubuntu drive D:!
please help me!:confused::confused:
thanks.
*Note: i can access drive D: from windows and is working fine...

---

### Post by ejay563 on 2008-05-06
Open up the terminal, and type

```
$ sudo fdisk -l
```

copy the resulting text, and post it.

---

### Post by Meydanb on 2008-05-07
i did it and it says this:
> User meydanb may run the following commands on this host:
    (ALL) ALL

is this the result? or there is something wrong?

---

### Post by HotShotDJ on 2008-05-07
> **Meydanb said:**
> now. i started it and played around, and i noticed that in Places-->computer i do not see my other partition D: on which ubuntu is installed on.
i just have 15.7 GB Media my CD-Roms, floppy and "FileSystem".
i cannot access from anywhere in ubuntu drive D:!
please help me!Linux does not label drives the same way that MSDOS/WINDOWS does.  There is no "Drive D:" as you are used to seeing it.  The drive labeled "FileSystem" is what you are looking for.

---

### Post by didac on 2008-05-07
>  i did it and it says this:
Quote:
User meydanb may run the following commands on this host:
(ALL) ALL
is this the result? or there is something wrong?


meydanb: you typed

```
sudo -l
```

you forgot fdisk in between. Don't worry and type again

```
sudo fdisk -l
```

---

### Post by Meydanb on 2008-05-07
allright, thanks allot for the help, found it under FileSystem\Host...
thanks again.
by the way, to run games, do i need a special version for linux?, it can play EXE Files?

---

### Post by ejay563 on 2008-05-07
IF you install wine, it can run some windows applications, but mostly you'll have to stick with windows for games. Although some people have lots of fun trying to get things to work in wine, so maybe you could be one of those and be adventurous.

---

### Post by ejay563 on 2008-05-07
> **ejay563 said:**
> IF you install wine, it can run some windows applications, but mostly you'll have to stick with windows for games. Although some people have lots of fun trying to get things to work in wine, so maybe you could be one of those and be adventurous.
Also, if you are playing old abaondonware DOS games, dosbox works rather well for that.

---

### Post by Meydanb on 2008-05-07
ok! thanks allot, i will give this wine thingi a try.
thanks ALLOT for the help!
Cheers.

---

