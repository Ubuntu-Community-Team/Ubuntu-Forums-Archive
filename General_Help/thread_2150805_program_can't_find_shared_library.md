---
title: "program can't find shared library"
date: 2013-06-02
forum: General Help
---

### Post by joetait on 2013-06-02
Hi


I purchased the latest humble bundle and I tried to get Thomas was alone working. I downloaded the .tar file, extracted it to my Desktop. I then made it executable (for sake of ease I just used ```
chmod 777 thomasWasAlone
```


When I try to run it from the terminal, with ```
./thomasWasAlone
``` I get the following output

```
joe@Daisy:~$ Desktop/thomasLinuxStandalone/thomasWasAlone
Desktop/thomasLinuxStandalone/thomasWasAlone: error while loading shared libraries: libXcursor.so.1: cannot open shared object file: No such file or directory
```


I have installed libxcursor1 and libxcursor1-dbg though, so I am not sure why it can't find them. If anyone has any insight it would be much appreciated


Thanks in advance


Joe


Edit - I have checked the checksum too btwH

---

### Post by ShadowVegan on 2013-06-02
If it's a shared file maybe it requires root? Did you try typing sudo at the beginning of the command?
```
sudo Desktop/thomasLinuxStandalone/thomasWasAlone
```

---

### Post by joetait on 2013-06-02
Hi there

Yeah, I did try that, but I got exactly the same error.

Thanks for the suggestion though :)

---

### Post by steeldriver on 2013-06-02
I don't know anything about Humble Bundles but based on the dir name 'thomasLinuxStandalone' I'm guessing this ships with its own .so libraries rather than using the system supplied ones?

Although your post says your are executing ./thomasWasAlone, you actually appear to be in your home directory ~ and are executing with a relative path from there i.e. as Desktop/thomasLinuxStandalone/thomasWasAlone - that's not quite the same thing, if the bundle has hardwired relative paths for libraries (for instance, it may be expecting to find libXcursor.so.1 at ../lib relative to the current directory)

My guess would be to try changing to the actual thomasLinuxStandalone dir and trying from there - unless there's a README file that tells you otherwise

```

cd Desktop/thomasLinuxStandalone
./thomasWasAlone

```

OTOH if it is looking for a system-supplied libXcursor.so.1 library, you can check if it's installed with

```
apt-cache policy libxcursor1
```

---

### Post by joetait on 2013-06-02
Hi Steeldriver


I have tried starting in the directory too, but unfortunately to no avail. I get exactly the same error. And the libraries are certainly installed. Thanks anyway though :)

---

### Post by Cheesemill on 2013-06-02
Are you running a 64-bit install by any chance?

If you are then the game is probably looking for the 32-bit versions of the libraries, which you may not have installed.
If this is the case then try installing them...
```
sudo apt-get install libxcursor1:i386 libxcursor1-dbg:i386
```

---

### Post by joetait on 2013-06-02
Cheesemill, that is superb. Works perfectly now, thank you very much!

---

### Post by RayDeCampo on 2013-07-20
Thanks Cheesemill, helped me as well.

---

