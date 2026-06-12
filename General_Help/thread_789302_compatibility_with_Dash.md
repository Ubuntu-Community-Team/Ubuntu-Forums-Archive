---
title: "compatibility with Dash"
date: 2008-05-10
forum: General Help
---

### Post by guix on 2008-05-10
Hi,

I'm concerned by the compatibility of a few scripts I have on a computer under Gutsy. These are quite simple bash scripts : backup with Rsync of local directories and distant directories via SSH, mysqldumps, I also have some datamining scripts and file renaming scripts, image procession, ...

Is there a risk that the script show up incompatible with Dash ? To create the scripts I looked on the web for snipets of bash scripts so I couldn't say if they are POSIX compliant. The level of the scripts is quite low so on the one hand I guess they should be compatible, on the other hand I'm trying to be pessimistic and tell myself that maybe the scripts are very simple because they don't follow POSIX.

I can post the scripts but there are maybe 5 or 10, so a bit of work for you. I'm looking for a general answer.

Thanks :)

---

### Post by Vivaldi Gloria on 2008-05-30
If your script starts with

```
#!/bin/bash
```

and it is executable then AFAIK there is a difference between

```
sh script
```

and

```
./script
```

The first one uses dash to run your script regardless of the #!/bin/bash line because /bin/sh links to dash. 

The second one uses bash because of the #!/bin/bash line.

So if you want to run your scripts with bash then include the #!/bin/bash line and call them by name.

---

### Post by guix on 2008-06-07
Thanks a lot for this explanation !

---

### Post by Vivaldi Gloria on 2008-06-07
You're welcome.

---

