---
title: "gnu cp order?"
date: 2008-02-18
forum: General Help
---

### Post by sammydee on 2008-02-18
Hi all

Does anyone know what order that the cp command that comes with linux copies files recursively in?

Is it alphabetical, ie finish directory A completely then start directory B etc?

Or does it have another way of doing it?

sam

---

### Post by corney91 on 2008-02-18
I'm pretty sure it's alphabetical:
```
dan@dan-laptop:~$ mkdir test
dan@dan-laptop:~$ cd test/
dan@dan-laptop:~/test$ mkdir ../test2
dan@dan-laptop:~/test$ mkdir a b c d
dan@dan-laptop:~/test$ ls
a  b  c  d
dan@dan-laptop:~/test$ cp -rv * ../test2/
`a' -> `../test2/a'
`b' -> `../test2/b'
`c' -> `../test2/c'
`d' -> `../test2/d'

```

Just did it with numbers as well - numbers go first.

---

### Post by danwood76 on 2008-02-18
I think it does it in the order they appear on the disk.
ie order of creation.

to test create the same dirs again but in a different order and you will get them copied in the order they were created.
(I just tested on my machine)

---

### Post by corney91 on 2008-02-18
> **danwood76 said:**
> I think it does it in the order they appear on the disk.
ie order of creation.

to test create the same dirs again but in a different order and you will get them copied in the order they were created.
(I just tested on my machine)
:confused:
Mine still does does it in alphabetical order:```
dan@dan-laptop:~/test$ mkdir q w e r t y u d f g h a
dan@dan-laptop:~/test$ mkdir 6 2 5 1 5 3 2 1
mkdir: cannot create directory `5': File exists
mkdir: cannot create directory `2': File exists
mkdir: cannot create directory `1': File exists
dan@dan-laptop:~/test$ ls
1  2  3  5  6  a  d  e  f  g  h  q  r  t  u  w  y
dan@dan-laptop:~/test$ cp -rv * ../test2/
`1' -> `../test2/1'
`2' -> `../test2/2'
`3' -> `../test2/3'
`5' -> `../test2/5'
`6' -> `../test2/6'
`a' -> `../test2/a'
`d' -> `../test2/d'
`e' -> `../test2/e'
`f' -> `../test2/f'
`g' -> `../test2/g'
`h' -> `../test2/h'
`q' -> `../test2/q'
`r' -> `../test2/r'
`t' -> `../test2/t'
`u' -> `../test2/u'
`w' -> `../test2/w'
`y' -> `../test2/y'

```

As seperate mkdir commands:
```
dan@dan-laptop:~/test$ mkdir h
dan@dan-laptop:~/test$ mkdir w
dan@dan-laptop:~/test$ mkdir q
dan@dan-laptop:~/test$ mkdir a
dan@dan-laptop:~/test$ mkdir 8
dan@dan-laptop:~/test$ mkdir 1
dan@dan-laptop:~/test$ mkdir 9
dan@dan-laptop:~/test$ cp -rv * ../test2/
`1' -> `../test2/1'
`8' -> `../test2/8'
`9' -> `../test2/9'
`a' -> `../test2/a'
`h' -> `../test2/h'
`q' -> `../test2/q'
`w' -> `../test2/w'

```

Of course, this is assuming it is done in the order it is showing it being done...

---

### Post by sammydee on 2008-02-18
Ahh, I think it is alphabetical then. That would make the most sense.

Ok thanks.

Sam

---

### Post by danwood76 on 2008-02-18
> **corney91 said:**
> :confused:
Mine still does does it in alphabetical order:

thats odd.
earlier mine did it in the order I created the directories.

alphabetical would make the most sense tho.
maybe my laptop was having a funny moment.

---

### Post by seventhc on 2008-02-18
when I created these at the same time it wouldn't sort them by time created, but creating them individually it did sort them using ls -u
```

j0hn@cipher:~/test$ mkdir a
j0hn@cipher:~/test$ mkdir c
j0hn@cipher:~/test$ mkdir b
j0hn@cipher:~/test$ mkdir d
j0hn@cipher:~/test$ ls -u
d  b  c  a
j0hn@cipher:~/test$ 

```
never mind, I think this is different from what you were asking.

---

