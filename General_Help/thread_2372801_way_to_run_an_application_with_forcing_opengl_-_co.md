---
title: "way to run an application with forcing opengl - commandline"
date: 2017-09-28
forum: General Help
---

### Post by someoe on 2017-09-28
hi

i have been wondering who to "force opengl " with ubuntu applications because my mesa is low and i found it but now i had forgot the command  to do that and reinstalled ubuntu(there's no way to check the terminal history" , the command was looking like these :

```
$ "something" LIBGL(or force-opengl)_ALWAYS_SOFTWARE "something" ./the_program_name
``` i do these command in the game directory then press "Enter" after a long output appears and the game opens correctly and without problems (but with low, so i want any help with the command name, it's like "-opengl" parameter in wine but in linux ?

thanks

---

### Post by someoe on 2017-09-28
I'm sorry for messing around -_-

but i had realized that the first command i had found is correct and there's no need to remember it :

```
$ LIBGL_ALWAYS_SOFTWARE=1 ./the_program_name
```

---

