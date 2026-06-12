---
title: "Installed program not executing"
date: 2017-09-26
forum: General Help
---

### Post by feefle on 2017-09-26
I installed a bioinformatic program . After doing sudo chmod a+x /usr/local/bin/program, it shows me : bash: /usr/local/bin/program: No such file or directory.

I have access to user bin.

Any help?

---

### Post by TheFu on 2017-09-26
Insufficient information provided to help.  Things installed don't automatically get placed somewhere.  How was it installed? What directions were followed?  Any errors?  

Blindly assuming a file is in some directory isn't helpful.
```

ls -la /usr/local/bin/program
```
Does that show something is there?

---

### Post by ajgreeny on 2017-09-26
I assume you did not actually type **/usr/local/bin/program** when you used that chmod command?

Presumably the executable of the bioinformatic program is called something other than **program** and if you are simply following an example for such a command, that word may have been used as just that; an example only.

I might also help to know exactly what it was that you installed, where it came from and how you installed it.

---

