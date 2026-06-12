---
title: "how to unlock a folder -rwxr-xr-x must be drwxr-xr-x"
date: 2019-04-06
forum: General Help
---

### Post by creatxr on 2019-04-06
how to unlock a folder -rwxr-xr-x must be drwxr-xr-x

my service "start request too quickly", and it was locked.

i found that the folder permissions is changed to -rwxr-xr-x

if i can modify it to drwxr-xr-x , i think the service will work.

how to do to add "d" ?

thanks

---

### Post by TheFu on 2019-04-06
**mkdir** - but if there is a file with the same name there, it won't work.  Just move the existing file to any different name and run mkdir.
I know of no method to magically change a file into a directory using permissions.  Having a strong grasp of Unix permissions is mandatory to make any Unix work for you.

I'm suspicious that either your claim is being misinterpreted or there is a file system failure which could be disk, cable, or logical. Can't say.

---

