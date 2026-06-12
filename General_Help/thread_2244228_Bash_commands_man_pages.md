---
title: "Bash commands: man pages"
date: 2014-09-14
forum: General Help
---

### Post by ric_Poirier on 2014-09-14
Hi everyone,

I have recently been learning to write bash scripts. In one of the script, I wanted to ask the user to type in some info. To do this, I used the **read** command.

Then, to know more about the **read** command, I typed, in the terminal: ```
man read
```

I found out that the **read** command in the man pages has nothing to do with the one I used in my bash script. Now my question is this: is there a way to see the man pages of the **read** command I use in my bash scripts (or any other bash commands)?

Thanks a lot.

---

### Post by steeldriver on 2014-09-14
Since 'read' is a shell built-in, you need to look in the man page for bash itself
```

man bash

```

or use the built-in help function from within the shell

```

help read

```

---

### Post by vasa1 on 2014-09-14
And you may find this a bit more friendly than the man pages: mywiki.wooledge.org/BashGuide

---

### Post by ric_Poirier on 2014-09-15
> **steeldriver said:**
> Since 'read' is a shell built-in, you need to look in the man page for bash itself

Tnak you very much!

---

