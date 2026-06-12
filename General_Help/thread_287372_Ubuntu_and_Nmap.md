---
title: "Ubuntu and Nmap"
date: 2006-10-28
forum: General Help
---

### Post by fifth_5 on 2006-10-28
Ok, i have installed nmap, and it seemed to install fine. But when i come to run it it throws back this error 

nmap: error while loading shared libraries: libpcre.so.0: cannot open shared object file: No such file or directory

not sure what to do on this one. Andy help would be cool.

Thanks 

fifth

---

### Post by vibestriton on 2006-10-28
```
sudo apt-get install libpcre3 libpcre3-dev
```

Does that do the trick?

---

### Post by fifth_5 on 2006-10-28
Na after installing it still throws back the same error.

thanks

fifth

---

### Post by fifth_5 on 2006-10-28
I have tried installing extra packages on this 1, just cant get it to work. really need help on this 1 guys.

thanks

fifth

---

### Post by vibestriton on 2006-10-28
```
sudo apt-get install --reinstall nmap
sudo ln -s /usr/lib/libpcre.so.3 /usr/lib/libpcre.so.0
```

---

### Post by fifth_5 on 2006-10-28
Thanks for that, i owe you big time.

take care 

fifth

---

