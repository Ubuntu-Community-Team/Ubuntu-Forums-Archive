---
title: "how to create multi zip files"
date: 2007-05-26
forum: General Help
---

### Post by dophine on 2007-05-26
hi,

I want to zip a big a file to  multi smaller size zip file. how can I do that?

thank you

---

### Post by dachinster on 2007-11-11
hi guys, i see there is a thread about this already so instead of starting another, i just wanted to follow up with this...

i have an 8GB file and i want to zip/tar it across 2 dvds.
i need to make them small enough to fit on a standard dvd

anyone knows how to create a multi volume zip file?

---

### Post by mali2297 on 2007-11-11
> **dachinster said:**
> hi guys, i see there is a thread about this already so instead of starting another, i just wanted to follow up with this...

i have an 8GB file and i want to zip/tar it across 2 dvds.
i need to make them small enough to fit on a standard dvd

anyone knows how to create a multi volume zip file?

Assume that you want to use tar to archive and compress a file **foo** of size 8 GB. Type commands
```

tar -cvzf foo.tar.gz foo
split -d -b4000m foo.tar.gz foo.tar.gz.

```
Then you will have two files **foo.tar.gz.00** and **foo.tar.gz.01** of size 4 GB maximum each.

To extract **foo** from the split compressed archive:
```

cat foo.tar.gz.* > foo.tar.gz
tar -xvzf foo.tar.gz

```

Of course, you could skip tar and just split the original file:
```

split -d -b4000m foo foo.

```
and join the pieces later with
```

cat foo.* > foo

```

---

### Post by dachinster on 2007-11-11
o, my mistake, it is actually a directory of files that needs compressing.
will the above still work?
once of the files inside that directory is an ISO file 7.8GB big but I need the accompanying files to go with it

---

### Post by mali2297 on 2007-11-11
> **dachinster said:**
> o, my mistake, it is actually a directory of files that needs compressing.
will the above still work?
once of the files inside that directory is an ISO file 7.8GB big but I need the accompanying files to go with it

Yes, you can create a compressed tar file with same command if foo is a directory. The file foo.tar.gz can then also be split as before.

Alternatively, tar can itself construct multivolume archives if you don't use compression:
```

tar -cvL4000000 -f foo.tar.00 -f foo.tar.01 foo

```
..to extract:
```

tar -xvM -f foo.tar.00 -f foo.tar.01

```

As you can see, the possibilities are numerous. :-)

---

### Post by inversekinetix on 2007-11-11
> **mali2297 said:**
> Yes, you can create a compressed tar file with same command if foo is a directory. The file foo.tar.gz can then also be split as before.

Alternatively, tar can itself construct multivolume archives if you don't use compression:
```

tar -cvL4000000 -f foo.tar.00 -f foo.tar.01 foo

```
..to extract:
```

tar -xvM -f foo.tar.00 -f foo.tar.01

```

As you can see, the possibilities are numerous. :-)

is there a gui way to do that?

what does foo mean?

---

### Post by mali2297 on 2007-11-12
> **inversekinetix said:**
> is there a gui way to do that?

Some people recommend **7zip** but I haven't tried it myself.

> 
what does foo mean?

Change it to the name of your directory (or file).
From [Wikipedia]("http://en.wikipedia.org/wiki/Foo"):
> 
The word foo itself has no meaning and is merely a commonly used logical representation that is used much like the letters 'x' and 'y' in algebra.


---

### Post by rasmusbp on 2007-11-26
Please - there must be a simpler way. Isn't there any archiving application with a GUI that will give you the option of creating more multiple zip files? Like any zip program in XP would have. Anyone?

Thanks.
Rasmus

---

### Post by mali2297 on 2007-11-26
> **rasmusbp said:**
> Please - there must be a simpler way. Isn't there any archiving application with a GUI that will give you the option of creating more multiple zip files? Like any zip program in XP would have. Anyone?

Thanks.
Rasmus

You could try this:
[http://ubuntuforums.org/showthread.php?t=556756](http://ubuntuforums.org/showthread.php?t=556756)

---

### Post by rasmusbp on 2007-11-26
great tip, thanks a lot!! :)

---

### Post by mali2297 on 2007-12-01
I just found [PeaZip]("http://www.peazip.org/"), it might be worth to try for those who shun the CLI.

---

