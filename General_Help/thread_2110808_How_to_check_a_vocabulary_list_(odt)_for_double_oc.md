---
title: "How to check a vocabulary list (odt) for double occurance of words?"
date: 2013-01-31
forum: General Help
---

### Post by kairo1 on 2013-01-31
hello everyone,
this is not necessarily ubuntu related but i am still hoping to find help.

i have a long list of English terms i collected over years and saved as odt file. 
through combining lists saved in various folders many words occur  twice.
How can i find and delete them to have a structured list?
much thanks in advance

---

### Post by Bucky Ball on 2013-01-31
Welcome to the forums. In Open or Libre Office:

Edit>Find & Replace (or Find probably works the same).

You can look for more than one word at a time, short phrases even. Not sure what the limit is. For instance.

Find 'the end'.

You don't need to replace it with anything but you could replace it with space if you left the 'replace' box empty, I guess.

---

### Post by steeldriver on 2013-01-31
it would probably be easier if you sort the list

```

 apple
 aardvark
 dog
 cat
 leopard
 Cat
 aardvark

```Select all (e.g. Ctrl-a)
Tools --> Sort
Alphanumeric

```

 aardvark
 aardvark
 apple
 Cat
 cat
 dog
 leopard
  
```

Or if you want to get unixy, you could save the file as text and then do a case-insensitive 'sort unique'

```
$ sort -fu wordlist.txt 
aardvark
apple
cat
dog
leopard
```

---

