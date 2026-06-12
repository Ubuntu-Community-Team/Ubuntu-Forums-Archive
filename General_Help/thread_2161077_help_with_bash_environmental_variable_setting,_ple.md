---
title: "help with bash environmental variable setting, please"
date: 2013-07-09
forum: General Help
---

### Post by jamaas on 2013-07-09
I'm attempting to install a package called kpp (kinetic preprocessor) which is a fortran90 based package. The installation instructions are a bit dated so the correct specification might have changed.  

in my user directory (~) I created a subdirectory called "kpp" and untarred all the files into it.  I then ran the "make" and all seemed to got well.  It creates and executable simply named "bin" in this directory.  

As per the instructions I put this in my .bashrc, which is also located in ~

------------------------

## stuff for KPP, kinetic preprocessor

export kpp_HOME=$HOME/kpp
export PATH=$PATH:$kpp_HOME/bin

------------------------

However when I open a new terminal and try typing "kpp" it doesn't find it, or any of the associated directories/files.  Is there something wrong with my environmental variable specification?

Thanks

J

---

### Post by Kujua on 2013-07-09
Your env variables look okay. What error are you getting when you try to run the command? Can you post the output of following commands?
```
echo $PATH
ls -l $kpp_HOME/bin

```

---

### Post by jamaas on 2013-07-09
Thanks,

This is the output.

$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/home/jim/kpp/bin

$ ls -l $kpp_HOME/bin
-rwxrwxr-x 1 jim jim 352602 Jul  9 13:05 /home/jim/kpp/bin

-------------------

J

---

### Post by steeldriver on 2013-07-09
Well as you mentioned in your first post the 'make' seems to have created an executable called 'bin' whereas the PATH instructions assume it would create a *directory* called 'bin' and put the executable (called 'kpp') *inside* it - most likely a wrinkle in the 'make' process somewhere

You *could* change the export instruction to 'export PATH=$PATH:$kpp_HOME' and then run the program by typing 'bin' but imho that would be confusing - I suggest you either try to fix the build process so that things get the expected names or manually rename the executable and create a bin directory to put it in (the latter might not work if it there are dependent libraries that are not where the moved executable expects them to be, due to relative paths)

---

### Post by jamaas on 2013-07-09
Thanks again.

I took the second option and it works!  I'm not game to try to fix 'make' files  but created a new subdirectory /kpp/bin and then put the original executable bin file in it.  I renamed the executable to kpp and now it seems to work.

Thanks a bunch!

J

---

