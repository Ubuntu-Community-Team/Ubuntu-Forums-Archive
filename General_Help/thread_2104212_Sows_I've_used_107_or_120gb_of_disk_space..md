---
title: "Sows I've used 107 or 120gb of disk space."
date: 2013-01-12
forum: General Help
---

### Post by SirBartholomew on 2013-01-12
Hi My computer shows I have used 107gb of 120 diskspace. I have an ssd. It shows my home file is where it is used. I record music so there are some really big files but I have sent them all to trash and emptied trash. I do that regularly. I don't know if trim is not enabled or what. Any help would be appreciated.

---

### Post by steeldriver on 2013-01-12
You could search for large files in /home with something like

```
 $ sudo find /home -type f -size +1G
```

(adjust the '1G' as appropriate) - some people have found that their ~/.xsession-errors have grown huge but let's see

---

### Post by SirBartholomew on 2013-01-12
Are you sure that's the right comandline? I wont run with the $ do I need to cd to home? I ran with out and this is what it outputted.
```
find: paths must precede expression: size
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]
bart@BartsComputer:~$ sud
```

---

### Post by SirBartholomew on 2013-01-12
Ok I ran it from the home directory and got the error you were talking about . How would I adjust the 1g?

Just been learning about discard and things like that there is nothing in my fstab file?

---

### Post by dualslash on 2013-01-19
I ran into an issue where my hard drive was suddenly full. It turned out that my .xsession-errors.old was over 170 gb. You might want to check out that file. Its located in your home folder all you have to do is hit ctrl+h to show hidden files.

---

