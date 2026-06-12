---
title: "vtune under Hardy"
date: 2008-05-14
forum: General Help
---

### Post by toastmaker on 2008-05-14
Hello,

I've been trying to install and run Intel's vtune on Ubuntu 8.04 and embed it into eclipse. The installation doc says that it supports Ubuntu 7.10, but in Hardy it failes when trying to run. It seems that problems are caused by cross-referencing libraries and slight incompatibility with gcc-4.2, or maybe I am wrong...

/opt/intel/vtune/bin/vtlec
/opt/intel/eclipsepackage/3.2.1/eclipse/eclipse: /opt/sag/gcc-3.3/lib32/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/opt/intel/eclipsepackage/3.2.1/eclipse/eclipse: /opt/sag/gcc-3.3/lib32/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

- I use vtune version of eclipse tool, if I setup to integrate vtune into my existing version of eclipse, running it throws a core.
- I use sun's java jre-1.6
- I have both gcc-3.4 and gcc-4.2 installed

I don't understand why /opt/sag/gcc-3.3 looks for gcc-3.4.

Please, how can I link my own gcc libraries into /opt/sag directory created by vtune? Would this be a solution? 

Please, does somebody have some experience with successful running vtune under ubuntu 8.04? I am a linux newbie, please be patient with me :)

Thank you,

Martin

---

### Post by crazychopsticks on 2008-05-20
Hey,

I've been trying to get it installed as well and I get exactly the same problems. I don't know what to do to fix it. Might try to install in a supported distro and find a fix. Would love to hear from you if you manage to fix it though.

David

---

### Post by crazychopsticks on 2008-05-20
Hello,

I just played for a little bit and I have the program executing so far. I haven't tested it because I haven't managed to sort out the groups properly so far, I can only execute as root.

What I did (as root):

```

apt-get install gcc-3.3 

cd /opt/sag/gcc-3.3/lib32/

mv libgcc_s.so.1 /tmp/libgcc_s.so.1

ln /usr/lib/gcc-lib/i486-linux-gnu/3.3.6/libgcc_s.so libgcc_s.so.1


```

That got it executing for me as root.

How did you manage to properly add yourself to the required group?

Thanks
David

---

### Post by toastmaker on 2008-05-24
Thanks, I don't know yet if the functionality of vtune is ok, but after the linking you suggested it runs the gui.

Be careful and backup your projects, vtune somehow disrupted the configuration of files in my 'managed C code' project.

Ad groups: I simply add user to the group through System->Users and Groups... unlock by entering the password and add myself to the vtune group. I think it works since next login. Or a
```
# sudo usermod -g vtune username
``` should work as well.

m

---

### Post by lenorin on 2008-06-05
That was IMMENSELY helpful, thank you. Worked fine for me. Running vtune under my own username and everything. useradd <username> vtune should do it. Then remember to log off and log back on.

Thanks again!

---

### Post by wolfie2x on 2008-07-10
> **crazychopsticks said:**
> 
```

apt-get install gcc-3.3 

cd /opt/sag/gcc-3.3/lib32/

mv libgcc_s.so.1 /tmp/libgcc_s.so.1

ln /usr/lib/gcc-lib/i486-linux-gnu/3.3.6/libgcc_s.so libgcc_s.so.1


```


This got me around the 'GCC_3.4 not found' error, but eclipse would just crash soon after it loads the vtune perspective. also tried with SUN java 1.6.0_06-b02 but still crashes. :(
any help?

---

