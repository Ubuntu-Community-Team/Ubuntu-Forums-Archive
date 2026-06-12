---
title: "Sudden &quot;Invalid MIT-MAGIC-COOKIE-1&quot; when I run mpirun"
date: 2021-01-22
forum: General Help
---

### Post by kvothetheraven on 2021-01-22
[SIZE=2][COLOR=#242729]Suddenly whenever I run mpirun I get the error ```
Invalid MIT-MAGIC-COOKIE-1 key [/COLOR][/SIZE]
```[SIZE=2][COLOR=#242729]. I think this might have started after I killed a command using mpirun that had been launched from a python console.[/COLOR]
[COLOR=#242729]I looked at $XAUTHORITY and found noXauthority file. I also tried ```
xhost +local:
``` in the terminal since it was suggested somewhere but the problem remains.[/COLOR]
[COLOR=#242729]I have only used mpirun to run things locally on my pc. [/COLOR]
[COLOR=#242729]For the most part mpirun does still seem to do what it is supposed to, but I believe it also now creates errors in things that were working perfectly before.[/COLOR]
[COLOR=#242729]Simply running the below shows the warning for example (nonsense minimal example):
[/COLOR]
```
/usr/bin/mpirun -n 1 echo "bla"
```

I tried many things suggested on various websites such as creating a new .Xauthority file by the steps described in [https://superuser.com/a/941244/728074](https://superuser.com/a/941244/728074) and setting the $DISPLAY value to :0 or :0. Nothing helped. When I created a new .Xauthority file and then deleted it did give me instead the error ```
[FONT=Consolas]No protocol specified[/FONT]
```instead. I can go back to the magic cookie error by recreating the .Xauthority according to the steps in the above link.

System: Ubuntu 20.04 LTS

P.S.: I also asked the question on [/SIZE]https://unix.stackexchange.com/questions/630428/invalid-mit-magic-cookie-1-when-i-run-mpirun

---

