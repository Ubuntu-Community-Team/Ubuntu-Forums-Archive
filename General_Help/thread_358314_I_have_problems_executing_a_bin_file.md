---
title: "I have problems executing a bin file"
date: 2007-02-10
forum: General Help
---

### Post by ihatecommies on 2007-02-10
I'm trying to install Netbeans on Ubuntu. I have done that before without any problems, but now I can't ran the installation program jdk-6-nb-5_5-linux.bin.

chmod 777 jdk-6-nb-5_5-linux.bin doesn't work. Changing the owner doesn't work, nor changing the group.

I keep getting the following error message: "The launcher "bash" is not executable for the current user. Please give execute permission for the current user before attempting to launch the installer."

Even as root I get that message! And I'm pretty sure that root has all the rights, so what can I do about this?

---

### Post by sdide on 2007-02-10
Hey ,

Seems like you have trouble executing bash.

what does
```
$ ls -l `which bash` 
```
output?

---

### Post by ihatecommies on 2007-02-11
> **sdide said:**
> Hey ,

Seems like you have trouble executing bash.

what does
```
$ ls -l `which bash` 
```
output?

It gives me the following:

```
-rwxr-xr-x 1 root root 777584 2006-09-19 23:59 /bin/bash
```

But I have tried executing that file as root, doesn't work either.

---

### Post by gradedcheese on 2007-02-11
just to double-check, what your're doing is:

sudo ./jdk-6-nb-5_5-linux.bin

right?

---

### Post by ihatecommies on 2007-02-11
yes

---

### Post by gradedcheese on 2007-02-11
just a guess: try running it in bash (rather than dash, the 6.10 default shell)  That is, assuming you're using Edgy (6.10)

```

bash
sudo ./jdk-6-nb-5_5-linux.bin

```

---

### Post by sdide on 2007-02-11
Hey,

I am not sure  ... 
I downloaded the file from SUN Downloads, and got

```
/opt# md5sum jdk-6-nb-5_5-linux.bin 
e65fb583e4e0da8986277d7bfb531cb1  jdk-6-nb-5_5-linux.bin

/opt# file jdk-6-nb-5_5-linux.bin 
jdk-6-nb-5_5-linux.bin: awk script text

/opt# which awk
/usr/bin/awk

/opt# ls -l jdk-6-nb-5_5-linux.bin 
-rwxr--r-- 1 sdide sdide 137222144 2007-02-11 12:44 jdk-6-nb-5_5-linux.bin

/opt# echo $SHELL
/bin/bash

```

I had no trouble executing the file. Seems it would like a graphical interface, so you might  want to start it with gksudo.

Otherwise I don't know... if you have messed with /etc/sudoers try logging in as root instead of doing sudo.

Regards.

---

### Post by ihatecommies on 2007-02-11
I'm not a little further with that, I get now the following error message:

```
The installer is unable to run in graphical mode. Try running the installer with the -console or -silent flag.
```

I have tried to Google that, but I only get how I have to set the Display variable to 0:0, which I have done. So what now?

---

### Post by sdide on 2007-02-11
Be your normal user, the one logged in 
and do:

$ gksudo ./jdk-6-nb-5_5-linux.bin

give your password like normal sudo  - and away...

---

### Post by ihatecommies on 2007-02-11
> **sdide said:**
> Be your normal user, the one logged in 
and do:

$ gksudo ./jdk-6-nb-5_5-linux.bin

give your password like normal sudo  - and away...

That doesn't work, that also results into the following: ```
The installer is unable to run in graphical mode. Try running the installer with the -console or -silent flag.
```

What to do about that?

---

