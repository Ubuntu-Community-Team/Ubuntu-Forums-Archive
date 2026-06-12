---
title: "Bash help (variables)"
date: 2008-01-17
forum: General Help
---

### Post by PinkFloyd102489 on 2008-01-17
Ive looked over several bash howto's and none of them explain my problem Im having. I accidently broke file-roller in Nautilus so I decided to make a Nautilus script to replace it. Here it is:

```
tar cvzf $NAUTILUS_SCRIPT_SELECTED_URIS .tar.gz $NAUTILUS_SCRIPT_SELECTED_URIS | zenity --progress --pulsate --auto-close --auto-kill$

```


As you can see, Ive incorporated Zenity into it, just for a nice effect. The problem Im having is with the first Nautilus variable. I need to join the output of that variable, which is the file or directory name, with the .tar.gz. Any idea how?

---

### Post by PinkFloyd102489 on 2008-01-17
bump

---

### Post by johann_p on 2008-01-17
```
tar cvzf ${NAUTILUS_SCRIPT_SELECTED_URIS}.tar.gz 
```

The name sounds odd for that kind of use really: this variable does not really contain several URIS, does it?

---

### Post by PinkFloyd102489 on 2008-01-17
I dont know, it's just what Nautilus says to use to replace selected file names and directories.

That didnt do it. All it did was create a file called .tar.gz with the file inside. It didnt name it correctly.

---

