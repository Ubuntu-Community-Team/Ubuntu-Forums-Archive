---
title: "how to get cdrom name in command line"
date: 2007-08-01
forum: General Help
---

### Post by bortx on 2007-08-01
Hi,

I would like to obtain the name of the cdrom (volume label in windows) in the command line. Is there any command I can use for that?

Nautilus is getting this name successfully so I think It is possible through the command line

Thanks a lot!

---

### Post by Shib on 2007-08-01
hmm... not sure if there's a better way to do this... but it's the first line in /dev/hdc (or whatever device your cdrom is)

---

### Post by Shib on 2007-08-01
and here's a command that should/might work...

```
head -n 1 /dev/hdc | sed s/\ \ */\ /g | cut -d " " -f2
```

no guarentees... and change /dev/hdc to whatever your cdrom drive is... that worked for me though... YMMV :)

---

### Post by Shib on 2007-08-01
uh... might want to use

```
head -n 1 /dev/hdc | sed s/\ \ */~/g | cut -d "~" -f2
```

instead... that way you can have spaces in your title... but not ~'s... hmm

well, it's not the best way... but it's _a_ way at least :)

lol... uh, sorry for the spam... didn't notice the edit button until just now :(

---

### Post by bortx on 2007-08-06
thank you very much for your info.

By the way, could you please explain me the meaning of the command 

```
sed s/\ \ */~/g
```

I've seen that this comand is used on mode s/regexp/replacement/ but I cannot understand the regexp and replacement you used

Thanks a lot!

---

