---
title: "Running a command from .profile?"
date: 2021-01-27
forum: General Help
---

### Post by dbee on 2021-01-27
So i have exported my git profiles to .profile so i don't have to remember the directory every time from an emacs bash shell

I have a computer with very little hd and i run this command a lot ...
```

 du -a <dir> | sort -n -r | head -n 20

```
basically, it ranks folders in '/' in order of size.

I want to run this command by just typing ...

```

$SIZE /var 

```

where the $SIZE command would run the command above, and the '/var' would be the directory variable.

Looked on google. And in the emacs docs. can't find a solution. Any old hands out there know a little bash scripting and can help me out?

---

### Post by Keith_Helms on 2021-01-28
Add this to your .bashrc file

```
rank() {
    du -a "$1" | sort -n -r | head -n 20
}
```

Then you can just type

rank /some/directory/path

If you don't like "rank", call the function whatever you want

---

### Post by dbee on 2021-01-29
Excellent thanks Keith. 

That's easy. 

I want to mark this thread solved but can't on android :-(

---

### Post by QIII on 2021-01-29
"Thread tools" ->  "Mark this thread as solved" does not work?

---

### Post by QIII on 2021-01-29
That just worked fine for me on my phone.

---

