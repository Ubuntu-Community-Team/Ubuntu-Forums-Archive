---
title: "Help with selecting data of a file using commands"
date: 2008-06-04
forum: General Help
---

### Post by hadrien on 2008-06-04
Hi,

I'm so newby in Ubuntu and I have to treat with data in files and plot the results, but I have no idea of how to catch only the data I want...
For example, if I have these lines:

Search files for iddir = 3146 with 983 files in 166.672000 seconds | 166.678009635 CPU seconds.
1 - Search surls for lfn idfile = 6270 with 78 surls in 11.937000 seconds | 11.9413500878 CPU seconds.
2 - Search surls for guid idfile = 6270 with 78 surls in 0.47000 seconds | 0.0446548374165 CPU seconds.
1 - Search surls for guid idfile = 7400 with 78 surls in 11.688000 seconds | 11.6901882781 CPU seconds.
2 - Search surls for lfn idfile = 7400 with 78 surls in 0.47000 seconds | 0.0469255170699 CPU seconds.

And I want only the numbers information, in that way:
3146 983 166.672000 
what have I to do to select them and print them out in an other output file?

Thank you very much for your help!!

---

### Post by rampageoberon on 2008-06-04
Okay so if the whole file is formatted as follows

```
Search files for iddir = 3146 with 983 files in 166.672000 seconds | 166.678009635 CPU seconds.
```

Then you can get that output using the cut command. -d" " is space delimiter and -f tells it which fields

```
cut -d" " -f6,8,11 <inputfilename>
```

edit: to print in another file you could just redirect output

```
cut -d" " -f6,8,11 <inputfilename> > <outputfilename>
```

Hope that helps

---

### Post by hadrien on 2008-06-05
Thank you very much! I have solved the problem and I've learned a very useful command.

---

