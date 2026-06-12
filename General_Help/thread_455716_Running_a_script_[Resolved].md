---
title: "Running a script [Resolved]"
date: 2007-05-26
forum: General Help
---

### Post by dayfall on 2007-05-26
i have this script i have to run in the terminal called "cstart". and i am kind of new to this so i'm not sure exactly how it's done. i cd to the location of the file and when i type "cstart" and press enter, the terminal says that the file does not exist. i double checked, and it does. so i thought maybe there is some sort of command i have to run the script with. help me out please.

thanks in advance.

---

### Post by taurus on 2007-05-26
Try

```
./cstart
```

---

### Post by aysiu on 2007-05-26
I'm not sure, but you might have to make it executable first: ```
chmod +x cstart
``` and then execute it ```
./cstart
```

---

### Post by dayfall on 2007-05-26
ROFLMAO
i've been trying thousands of commands to no avail..

Thanks!

---

### Post by aysiu on 2007-05-26
If you put it in /usr/local/bin, it'll be executable universally: ```
sudo mv cstart /usr/local/bin/
``` then you can start it with the command ```
cstart
``` instead of first navigating to the folder where it lives and then doing ```
./cstart
```

---

### Post by dayfall on 2007-05-27
Awesome!
muchos gracias :D

---

