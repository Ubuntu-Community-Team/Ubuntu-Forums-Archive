---
title: "MATLAB 2012a no GUI"
date: 2013-02-08
forum: General Help
---

### Post by moicez on 2013-02-08
Hello to all Ubuntu community. I have several days trying to install Matlab. I have search a lot though the forums for the problem that I have and tried many "solutions", but none have worked.
So I have come to this forum with hopes that I can get this resolved once and for all.
Here is the situation:

I installed Matlab R2012a and gone through the activation process and everything looks fine. But when I try to run ./MATLAB I get this output:

```

Warning: Unable to load Java Runtime Environment: libjvm.so: cannot open shared object file: No such file or directory
Warning: Disabling Java support
Warning: latest version of matlab app-defaults file not found.
Contact your system administrator to have this file installed

                            < M A T L A B (R) >
                  Copyright 1984-2012 The MathWorks, Inc.
                    R2012a (7.14.0.739) 32-bit (glnx86)
                              February 9, 2012

 
To get started, type one of these: helpwin, helpdesk, or demo.
For product information, visit www.mathworks.com.
 
>> quit 
moises@moises-Studio-1535:/usr/local/MATLAB/R2012a/bin/glnx86$ 


```

When I type in the command java -version I get:

```

java version "1.7.0_13"
Java(TM) SE Runtime Environment (build 1.7.0_13-b20)
Java HotSpot(TM) Server VM (build 23.7-b01, mixed mode)

```

Also I should mention that I am running on Ubuntu 11.10 on 32bit.

I have read in some forums that is a problem with PATH variables but did not specify on how to fix it.

Please help ](*,)

---

### Post by moicez on 2013-02-09
AAhhhh! I finally made it work. Here is the solution:

There were two problems the Java one and the app-defaults. Both were a problem with environment variables.

The Java problem was fixed with:
```

export MATLAB_JAVA=<matlab_root_directory>/sys/java/jre/glnx86/jre

```

The app-defaults with:
```

export XAPPLRESDIR=<matlab_root_directory>/X11/app-defaults

```
And after that I was able to sleep comfortably :KS ):P

---

### Post by sandeepps4 on 2013-04-29
Hi moicez,

I tried your solution and it is working only for app-defaults error. I tried exporting both JRE within MATLAB installation folder and the one installed in my computer to MATLAB_JAVA variable. Even after trying these two, I'm not able have a MATLAB GUI. Still Java support is disabled when MATLAB running. Please let me know if you have thoughts. I'm running Matlab R2013 in Ubuntu 12.04 64 bit.

---

### Post by moicez on 2013-04-29
> **sandeepps4 said:**
> Hi moicez,

I tried your solution and it is working only for app-defaults error. I tried exporting both JRE within MATLAB installation folder and the one installed in my computer to MATLAB_JAVA variable. Even after trying these two, I'm not able have a MATLAB GUI. Still Java support is disabled when MATLAB running. Please let me know if you have thoughts. I'm running Matlab R2013 in Ubuntu 12.04 64 bit.

Hi there. Try setting the LD_LIBRARY_PATH variable also. Check my runnable script:

```

#!/bin/bash
export LD_LIBRARY_PATH="/usr/local/MATLAB/R2012a/runtime/glnx86:/usr/local/MATLAB/R2012a/bin/glnx86:/usr/local/MATLAB/R2012a/sys/java/jre/glnx86/jre/lib/i386/client":$LD_LIBRARY_PATH
/usr/local/MATLAB/R2012a/bin/glnx86/MATLAB

```

---

### Post by marco-cermatori on 2013-09-05
Hi Moicez,
I have got the same problem. What should I do after I create the environment variables? If I just run ./MATLAB again I get the same output.
Sorry I am not familiar with environment variables.
Thank you!

---

### Post by moicez on 2013-09-05
hey there,
wll you could try:
```

$ gedit ~/.bashrc

```

Then append this at the end:
```

export MATLAB_JAVA=<matlab_root_directory>/sys/java/jre/glnx86/jre
export XAPPLRESDIR=<matlab_root_directory>/X11/app-defaults
export LD_LIBRARY_PATH="/usr/local/MATLAB/R2012a/runtime/glnx86:/usr/local/MATLAB/R2012a/bin/glnx86:/usr/local/MATLAB/R2012a/sys/java/jre/glnx86/jre/lib/i386/client":$LD_LIBRARY_PATH
/usr/local/MATLAB/R2012a/bin/glnx86/MATLAB

```

after close and reopen the terminal OR do $ source ~/.bashrc

good luck!

---

### Post by marco-cermatori on 2013-09-06
It works!
Thank you very much indeed! :)
I just had to replace glnx86 with glnxa64 and i386/client with amd64/server.

---

### Post by julian-lebenhaft on 2013-12-07
Instead of launching the MATLAB gui via 
  /usr/local/MATLAB/R2013_Student/bin/glnxa64/MATLAB 
try
  /usr/local/MATLAB/R2013_Student/bin/matlab

I'm using an academic version of the software, but this should work for the professional version as well (just remove the _Student from the path). I'm running R2013a in Ubuntu 13.04 64 bit.

---

### Post by dct2 on 2014-07-06
> **marco-cermatori said:**
> It works!
Thank you very much indeed! :)
I just had to replace glnx86 with glnxa64 and i386/client with amd64/server.
can you show me your [COLOR=#000000][FONT=Ubuntu Mono]bashrc file? I have same [/FONT][/COLOR][COLOR=#000000]problem[/COLOR]

---

### Post by jorge12 on 2015-02-10
This answer worked for me. You need to run the executable from the matlab's: '/usr/local/MATLAB/whateverVersion/bin/matlab' since it is the one that it is compiled during the installation process.

---

