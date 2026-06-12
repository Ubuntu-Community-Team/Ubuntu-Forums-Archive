---
title: "Changing permission so that i dont have to sudo"
date: 2007-08-02
forum: General Help
---

### Post by phillips321 on 2007-08-02
i would like to run longrun as a basic user

which longrun
gives /usr/bin/longrun

ls -l /usr/bin/longrun
-rwxr-x--x 1 root root 11456 2006-06-20 11:43 longrun

sudo chmod 751 /usr/bin/longrun

when i try to run longrun i get 
longrun: must be run as root

i think it's because longrun needs to access 
/dev/cpu/0/cpuid and /dev/cpu/0/msr

cheers for anyone with any feedback

P.s. Longrun gives me the ability to dynamically scale the cpu frequency window to save battery on my laptop. I can use the program fine as root but what i want to do is run a script checking if the laptop is plugged in or not. (plugged in = allways run at 100%, battery = run in windows 0-50%) this will allow me to extend the use of my battery

---

### Post by nitro_n2o on 2007-08-02
don't change permission !!! 
use ```
sudo -i 
``` this will give you a root shell u have to type in your passwd only once.

---

### Post by phillips321 on 2007-08-02
will this allow me to run the line:

longrun -s 0 50

in a batch file?

---

### Post by nadalizadeh on 2007-08-02
go into a root shell
# cd to your program directory
#chmod 6755 myprogram
#chown root:root myprogram
# exit

$ /usr/bin/myprogram
   Hey you're root, Be carefull !!!
-------------------
Those commands just enables the "set userid on execution" and "set group id on execution"
now your program has always root permissions independent of who runs it !

---

