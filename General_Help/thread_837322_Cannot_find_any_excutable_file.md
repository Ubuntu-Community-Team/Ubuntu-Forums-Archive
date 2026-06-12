---
title: "Cannot find any excutable file"
date: 2008-06-22
forum: General Help
---

### Post by awalsh on 2008-06-22
Hello,

I have been a ubuntu user for many years and have very little problems with it. However recently I did a full reinstall and since then I cannot run any executable files from the terminal. It just says bash: <<filename>> no such file or directory.

I simply cannot understand why this is happening when the file can be seen by both my user and root, and before anyone asks they do have execute permissions on the file. Im really confused by this. 

Has anyone come across this before?

I am using Hardy 64bit on an Intel Q6700 which is brand new (that is why I reinstalled). I can run system programs like /usr/bin/vim but anything I download like F@H or Super PI throws up this error.

---

### Post by sp0nge on 2008-06-22
When you say executable file, I immediately think of "anyfile.exe". If this is the case, I believe this can only be done under WINE or some windows emulator environment. I don't believe Ubuntu (or linux in general) can natively run executable files.

---

### Post by spiderbatdad on 2008-06-22
I have certainly seen the error before. It usually pertains to being in the wrong working directory while trying to run a file not in my path. Try specifying complete paths and use sudo ./filename.<extension>

---

### Post by ddales on 2008-06-22
With the limited info available this sounds like a Path problem.

To find out why it's not working, first do:
which [filename_you_want_to_execute]

If it's not found, it's not in your $PATH environment variable.

echo $PATH  and make sure the path to the executable you want to use is present, if not, add it by adjusting your /etc/environment

You have to source the file after you make any changes to re-export the $PATH variable

---

### Post by awalsh on 2008-06-22
Its not an exe :) I mean a compiled Linux program that I have downloaded off say Folding @ Home. Below is an example from the terminal...

```

andrew@olympus:~/Desktop/FAH6.02beta1-Linux$ dir
fah6  mpiexec
andrew@olympus:~/Desktop/FAH6.02beta1-Linux$ ./fah6
bash: ./fah6: No such file or directory
andrew@olympus:~/Desktop/FAH6.02beta1-Linux$ 


```

---

### Post by sidheart on 2008-06-22
sorry i am not sure if i am in the correct discussion but can anyone of you please help me out!

I am new to ubuntu.can u help me to recover my boot partition's number as in: that (hd0,1) thing.

I want it to add a splash screen.

thanks a lot.

Siddharth

---

### Post by danwood76 on 2008-06-22
are you sure the permissions are correct?

do a 'ls -l' in the same directory and see if it has execute permissions.

---

### Post by spiderbatdad on 2008-06-22
```
./~/Desktop/FAH6.02beta1-Linux/fah6
``` If that doesn't work, try appending the filename with .sh, also make sure the shebang is on line #1

---

### Post by awalsh on 2008-06-22
SOLVED!!!!

I needed ia32 libs from synaptic. To enable 32bit applications.... this was strange as when I had an AMD X2 5000+ 64bit with Ubuntu 64bit I never had to install them. Hmmmm

---

### Post by danwood76 on 2008-06-22
Try an absolute path:
```

/home/andrew/Desktop/FAH6.02beta1-Linux/fah6

```
Its very odd, normally when the permissions are incorrect it says 'command not found'.
Its as if its not finding fah at all.
Are you sure its a 'good' copy of folding at home?

---

