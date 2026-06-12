---
title: "How do i append?"
date: 2014-12-23
forum: General Help
---

### Post by Entheo on 2014-12-23
Hello 

I need to append a file and i have found the file that i need to append and i have the code but i don't know how to go about it. In Linux mint i could do it easily but due to root actions being different on ubuntu i am stuck.

Thanks for any help in advance

---

### Post by steeldriver on 2014-12-23
Append what to what, exactly?

---

### Post by sudodus on 2014-12-23
Do you mean that you want to add data to the end of the file?

What file, what data, what program is creating the data?

If it is a text file with lines, and you want to add lines, like new lines to a log file, it is rather easy.

Example:

```
echo "this line" >> file.txt
```

adds a new line to the end of the file 'file.txt'.

---

### Post by Entheo on 2014-12-23
I am building new version of LMMS and there is a common fault which i am experiencing and the compiling instructions state:

**Note:**  On some Debian based systems if VST fails to locate wine-dev, append [COLOR=#000080]-DWINE_LIBRARY=/usr/lib/i386-linux-gnu/libwine.so[/COLOR] (this is exactly what is happening to me).

It is the root access i need to open containing folder and then to append code.

---

### Post by steeldriver on 2014-12-23
^^^ that probably just means append -DWINE_LIBRARY=/usr/lib/i386-linux-gnu/libwine.so to the `make` command line

---

### Post by sudodus on 2014-12-23
Maybe it means 'add that option to the command line or in the makefile', so that the compiler/linker can find it and use it.

---

### Post by Entheo on 2014-12-23
Sorry steel but how do i go about doing that? just add the line of code in the terminal after typing MAKE?

---

### Post by steeldriver on 2014-12-23
Can you provide a link to the instructions that you're following? if the build uses cmake, then it's probably a matter of running it as 

```

cmake -DWINE_LIBRARY=/usr/lib/i386-linux-gnu/libwine.so

```

---

### Post by Entheo on 2014-12-23
[https://github.com/LMMS/lmms/wiki/Compiling-lmms](https://github.com/LMMS/lmms/wiki/Compiling-lmms)


I am nearly there it is just this one problem that i want to sort out before i build and then i am finished.


The build code that confirms this particular problem with wine-dev is........

* VST-instrument hoster       : not found, please install (lib)wine-dev (or similiar) - 64 bit systems additionally need gcc-multilib and g++-multilib
* VST-effect hoster           : not found, please install (lib)wine-dev (or similiar) - 64 bit systems additionally need gcc-multilib and g++-multilib

and my wine-dev, gcc-multilib and g++-multilib is latest version.

---

### Post by steeldriver on 2014-12-23
OK so where it says

```

cmake .. -DCMAKE_INSTALL_PREFIX=../target 

```

make that

```

cmake .. -DCMAKE_INSTALL_PREFIX=../target **-DWINE_LIBRARY=/usr/lib/i386-linux-gnu/libwine.so**

```

---

### Post by Entheo on 2014-12-23
Just tried that but unfortunately it doesnt work. A message pops up saying that it needs to be pointed at the directory with all the correct files in it.

 Is there any way i can look at the directory...........**/usr/lib/i386-linux-gnu/libwine.so**? I have tried just to see if anything makes sense in there but i cannot open it as it says "archive type not supported". I wonder if i could paste the line in there?

---

### Post by steeldriver on 2014-12-23
/usr/lib/i386-linux-gnu/libwine.so isn't a directory - it's a shared object library file

Can you please cut'n'paste the exact error / terminal output that you are getting? preferably between [CODE] tags

---

### Post by Entheo on 2014-12-23
It is ok i have worked it out.........an cmake install txt file is created during build and i pasted line in there and it seems to of worked. The error said that it couldn't find a specific cmake txt file needed to run build (probably the one i appended with the code). In the cmake install file there was a line..... {DCMAKE_INSTALL_PREFIX} like on the link so i appended as per instructions and it is building fine now.

Thanks guys.........whew that problem was starting to do my head in then but fingers crossed all seems good.

Update: Build and install finished and LMMS working great!

---

