---
title: "Good resources for PATH?"
date: 2006-11-18
forum: General Help
---

### Post by Rybo on 2006-11-18
I'm trying to get firefox to be able to detect my realplayer and utilize more than just that one helix plugin for embedded media. I saw in another thread that the problem can be solved by altering the system PATH. Of course I didn't quite understand how to go about this. Are there any good tutorials out there on how to modify the PATH and especially on how to get the most out of realplayer? Any help would be appreciated.

---

### Post by David_T on 2006-11-18
You alter PATH by editing your .bashrc file and adding a line like:
```

export PATH=$PATH:/your/path/number/one:/your/path/number/two

```

Then you have to close and reopen your terminal.  Now try typing
```

echo $PATH

```
and you should see the new, expanded list of paths.

---

