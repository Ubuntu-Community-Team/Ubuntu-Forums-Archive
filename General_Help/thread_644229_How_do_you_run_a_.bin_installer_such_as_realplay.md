---
title: "How do you run a .bin installer such as realplay"
date: 2007-12-18
forum: General Help
---

### Post by lift_test on 2007-12-18
bzxcvz\dfv

---

### Post by smartboyathome on 2007-12-18
Ok... you run it by right clicking it > selecting the permissions tab, and then checking the checkbox next to Allow this to be run as a program. Then, open a terminal (make sure your script is in your home directory), and then run sudo ./filenamefor.bin. It should ask you to agree to their EULA then start installing it.

---

### Post by xrdguy on 2007-12-19
or u can open terminal and then go to folder where u have ur bash file. type

chmod +x  filename.bin

sudo ./filename.bin

---

### Post by lift_test on 2007-12-22
Thanks for replys
Doesn't work see read out

vic@TIME:~/Desktop$ chmod +x realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin
vic@TIME:~/Desktop$ sudo ./realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin
./realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
vic@TIME:~/Desktop$ 

Any idea what I,m doing wrong?

---

### Post by mellowd on 2007-12-22
Looks like you don't have the dependencies. 
```

sudo apt-get install compat-libstdc++-33
```


Then try again

---

### Post by lift_test on 2007-12-22
Thanks for help, this is what happened

vic@TIME:~/Desktop$ sudo apt-get install compat-libstdc++-33
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compat-libstdc++-33
vic@TIME:~/Desktop$ sudo ./realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin
./realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
vic@TIME:~/Desktop$ 

Looks like the, I presume libraries, weren't downloaded.  Any further help appreciated.

---

### Post by mellowd on 2007-12-22
hmm, wrong package.

try this

```
sudo apt-get install libstdc++5
sudo apt-get install libaio-dev
```

then try again

---

### Post by lift_test on 2007-12-22
Thats working but pardon my ignorance, what should be my response?

Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/home/vic/Desktop/RealPlayer]:

---

### Post by mellowd on 2007-12-22
I would assume the installer creates its own realplayer directory. As long as you have full write access to /home/vic you should be okay

---

### Post by lift_test on 2007-12-22
I thank you for your patience, what does this mean?

Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: ...y
enter the prefix for symbolic links [/usr]: ..................

---

### Post by mellowd on 2007-12-22
It's strange that realplayer would ask too many questions during the install. Try and accept all the defaults.

---

### Post by Krams on 2007-12-31
Thanks for the help with the apt-get command to get the lib. Your last recommendation to get stdlibc++5 and libaio-dev worked fine. After that the real player install proceeded. And as mentioned accepting the default for all the questions resulted in a successful install.

Thanks again
Krams:popcorn:

---

### Post by mellowd on 2007-12-31
Good to hear, mark the thread as closed :)

---

