---
title: "Compiling Issues with gaim, banshee and others..."
date: 2006-08-21
forum: General Help
---

### Post by pianoboy3333 on 2006-08-21
I recently noticed while trying to compile the latest svn/cvs (I don't remember which) of banshee, I got an error complaining about libxrender, but I choose to ignore it since it was an unstable version of banshee, but then when I went to compile 2.0.0b3.1 of gaim, I got the following error like the one from banshee:
```

grep: /usr/lib/libXrender.la: No such file or directory
/bin/sed: can't read /usr/lib/libXrender.la: No such file or directory
libtool: link: `/usr/lib/libXrender.la' is not a valid libtool archive
make[3]: *** [docklet.la] Error 1
make[3]: Leaving directory `/home/alex/Desktop/gaim-2.0.0beta3.1/plugins/docklet'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/alex/Desktop/gaim-2.0.0beta3.1/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/alex/Desktop/gaim-2.0.0beta3.1'
make: *** [all] Error 2

```

I have tried reinstalling the libxrender packages, I really have no idea what this could be, any help would be appreciated.

Programs that have failed:
Gaim 2.0.0 beta 3.1
Banshee 0.10.11
AllTray 0.69

---

### Post by pianoboy3333 on 2006-08-21
The only files that came up when I did a locate on libXrender were:

> 
/usr/lib/libXrender.so.1.3.0
/usr/lib/libXrender.so.1
/usr/lib/libXrender.a
/usr/lib/libXrender.so


---

### Post by ato on 2006-08-21
Same here.
i've tried lastest gaim and gphpedit.

Someone have a solution pls :-k

---

### Post by pianoboy3333 on 2006-08-22
I am now confirming, I can't compile the newest alltray, do these apps have something in common?

---

### Post by pianoboy3333 on 2006-08-22
Here's an error I got from compiling k3b 0.12.16:

```

make[4]: *** [libk3bffmpegdecoder.la] Error 1
make[4]: Leaving directory `/home/alex/Desktop/k3b-0.12.16/plugins/decoder/ffmpeg'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/alex/Desktop/k3b-0.12.16/plugins/decoder'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/alex/Desktop/k3b-0.12.16/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/alex/Desktop/k3b-0.12.16'
make: *** [all] Error 2

```

---

### Post by ato on 2006-08-23
I found this:
[http://www.ubuntuforums.org/showthread.php?t=238449]("http://www.ubuntuforums.org/showthread.php?t=238449")

For me it works.

---

