---
title: "gconftool-2: appending to a list"
date: 2006-12-21
forum: General Help
---

### Post by summersab on 2006-12-21
I'm trying to do a lot of things from the terminal. One of them is adding applets manually by editing gconf values using gconftool-2. I'm trying to edit the gconf key /apps/panel/general/applet_id_list. The type for this key is a string list. What I want to do is append a value to the list. The problem is that it already has existing values. If I simply --set a value to the list, I overwrite the whole thing and remove all applets from all panels (BAD STUFF HAPPENS). So, how do I use gconftool-2 to append a value to an existing list without biffing the contents of the list? Please do NOT tell me how to do this by clicking somewhere - I'm trying to write automated scripts, not something that requires user intervention and clicking. Thanks for the help!!!

---

### Post by 23meg on 2006-12-21
You can use I/O redirection to write it to a text file.```
gconftool-2 -g /name/of/key > filename
```More on redirection [here]("http://www.linuxcommand.org/lts0060.php").

---

### Post by koenn on 2006-12-21
I don't know the gconftool syntax - showing an example of what you're trying to do might help. 

something you might try is to save the old string in a variable, append to it, then use it again in a gconf statement.
Something along the lines of 
```

OLDVALUE=$(gconftool --get ... something something)
NEWVALUE="$OLDVALUE, addeditem1, addeditem2"

#set new value
gconftoom --set  ... ...  "$NEWVALUE"

```

---

