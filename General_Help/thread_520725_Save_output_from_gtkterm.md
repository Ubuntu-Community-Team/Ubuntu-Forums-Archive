---
title: "Save output from gtkterm"
date: 2007-08-08
forum: General Help
---

### Post by jonlemur on 2007-08-08
Hello, I'm trying to get the output from gtkterm to output not only to its window, but also to a file, so that it is saved immediately, rather than by my clicking to save every now and then.  I've tried 
```

gtkterm -f data.txt
```
hoping that that would save it to a file in my current directory.  I've also tried
```

gtkterm -f /home/$USERNAME/Desktop/data.txt 
```
hoping that that would save it to a specified folder.  Neither of those seem to be creating the file though, even if I quit out of gtkterm.  I've looked a little for a user manual for gtkterm and I've looked through the other posts, but I haven't been able to find anything to tell me how to do this.  Any ideas?

EDIT:
After rereading the man page, it appears that the -f option is definitely the wrong option for this, as it sends the file following the -f (let me know if I'm wrong about that).

---

### Post by misconfiguration on 2007-08-08
```
touch data.txt
gtkterm  >> data.txt
```

---

