---
title: "How to get libmotif3 working"
date: 2007-08-22
forum: General Help
---

### Post by 912R on 2007-08-22
Hi!
Have just converted to Ubuntu after many tries over the years to go for Linux. So far everything 
is working good, and it feels good..
I have one problem that i want to fix if someone has suggestions. I have a program that needs
libmotif3 to work good. It is also going on lesstif2 but much more unstable.
My problem is that i can not get libmotif3 to work.. I can install it but it does not seem to work.
I have an HP laptop with ubuntu32 on it.
Regards

---

### Post by manimal on 2007-08-22
Can you describe "does not seem to work" a bit more?  For example, does your program crash entirely?  Does it run, but use lesstif2 and not libmotif3?  Or does it complain and say it can't find libmotif3?

---

### Post by 912R on 2007-08-22
Thanks for reply!
The program that i need to use is recommended with libmotif3, but can work with lesstif2. But it hangs up more often with lesstif2.
When i install libmotif3 only, the program will not start. When i install lesstif2 the program starts. If i uninstall libmotif3, the program still starts with lesstif2..
Maybe I'm missing something in libmotif3 when i install it ?

---

### Post by manimal on 2007-08-22
Probably the best thing to do is install libmotif3 only and recompile your application.  However, I think there is a kludgey way to "make it work" also.  Install libmotif3 only and at the command line type:

```
ldd /full/path/to/executable
```

This will give a list of all the shared libraries your executable depends on (type "man ldd" at the command line for more info).  I suspect that one of the libraries will say "not found" or something like that.  That library will be the lesstif one, because your executable was compiled with lesstif but it is not installed.  Post the output of the above command and we'll figure it out from there.

---

### Post by 912R on 2007-08-22
Ok
Now lesstif2 is gone..
Libmotif3 is uptodate..
I start my application in terminal to see the fail notices..

Error: Could not register handle for external module X-UTILITIES::CAPIX11:
 libXm.so.2: cannot open shared object file: No such file or directory.
  1 (abort) Quit process.

Type :b for backtrace, :c <option number> to proceed,  or :? for other options

CL-USER 1 : 1 > 


?????:(

This is  the output of the ldd commando :

linux-gate.so.1 =>  (0xffffe000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f9f000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f88000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7e46000)
        /lib/ld-linux.so.2 (0xb7fb4000)

---

### Post by manimal on 2007-08-22
That wasn't what I was expecting!  In any case, at least now we know the name of the missing library - libXm.so.2.  The libmotif3 package provides "/usr/lib/libXm.so.3" and my kludgey fix is to make a symbolic link to this library with the name of the library that your app is looking for:

```
sudo ln -s /usr/lib/libXm.so.3  /usr/lib/libXm.so.2
```

Then, try your app.  I hope it works!

---

### Post by 912R on 2007-08-23
Fixed the link..
Now the program starts, but..

list some other problems in terminal:

Warning: unable to find default fallback resources for application class lispworks
Xt error: "could't find per display information"
Assuming: default-port-font

Warning: (xt warning) cannot find callback list in xtAddcallback
Warning: (xt warning) cannot find callback list in xtAddcallback
Warning: (xt warning) cannot find callback list in xtAddcallback
Warning: (xt warning) cannot find callback list in xtAddcallback



???

---

### Post by manimal on 2007-08-23
Does it work (ignoring the warnings)?

---

### Post by 912R on 2007-08-23
It's trying to start up but crashes..

Libmotif3 has to miss something that lesstif2 has, since it's working under lesstif2?

I have also send an request to the author of the app. for suggestions.

Here is an picture of the application when it starts up and it's fail warning..

[IMG][[IMG]http://img403.imageshack.us/img403/4333/screenshotwt0.th.png[/IMG]](http://img403.imageshack.us/my.php?image=screenshotwt0.png)[/IMG]

---

### Post by manimal on 2007-08-24
I searched for "X-UTILITIES::CAPIX11" on google.  Does this help?

[http://www.ozten.com/psto/2007/06/lispworks-on-x8664-ubuntu-feisty-i-was.html]("http://www.ozten.com/psto/2007/06/lispworks-on-x8664-ubuntu-feisty-i-was.html")

---

### Post by 912R on 2007-08-24
Hmm..
I have visited that link before, but it seems that it's for the amd64.
My computer is Amd64, but runs on ubuntu32.

Maybe openmotif should be installed? 
I will try to find an way to install this on the machine, and see what happens:)

The application says something with "capi extensions" is wrong. I don't know what this is, but i will look around and see..

---

