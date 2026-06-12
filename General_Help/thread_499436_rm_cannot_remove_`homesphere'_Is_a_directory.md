---
title: "rm: cannot remove `/home/sphere': Is a directory"
date: 2007-07-12
forum: General Help
---

### Post by Wuu on 2007-07-12
i can`t remove dir :(

[PHP]main@main-laptop:~$ sudo rm /home/sphere[/PHP]

or
[PHP]
sudo -i
rm /home/sphere[/PHP]
i get erro
rm: cannot remove `/home/sphere': Is a directory

---

### Post by greg_g on 2007-07-12
try "rm -rf /home/sphere"

the r is recursive and f is force

greg

---

### Post by sisco311 on 2007-07-12
```
sudo rm -r /home/sphere
```for more info 
```
man rm
```

---

### Post by rax_m on 2007-07-12
Or if a directory is empty than you ca do: ```
 rmdir /home/sphere 
```

I think it's a bit safer..

---

