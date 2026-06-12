---
title: "Twlog"
date: 2007-06-19
forum: General Help
---

### Post by malel on 2007-06-19
I have downloaded and installed 'twlog' a ham radio opr logging program but I am not able to start it up.
I am running Ubuntu 7.04 . Can someone please offer some help on this one . Thankyou

---

### Post by PaulFr on 2007-06-19
If your error message when running twlog looks like *twlog: error while loading shared libraries: libXbae.so.4: cannot open shared object file: No such file or directory*

then one way to solve it is as follows: **export LD_LIBRARY_PATH=/usr/local/lib; ./twlog**

To make this permanent, add the **export LD_LIBRARY_PATH=/usr/local/lib** part to the end of your ~/.bashrc file (using your favorite editor). Hope this helps.

---

### Post by malel on 2007-06-19
Thank for your reply but I cannot get twlog to even start. It has been installed but as it won't start I do not get any error messages. It is in /etc but even putting a path to it and a desktop icon it still will not start up. It is as though something is missing. I have downloaded and installed it before without any trouble. Maybe a library is missing .

Regards

---

### Post by PaulFr on 2007-06-19
To find out if any libraries required are missing, please open a terminal and type the command **ldd /etc/twlog**. This will check if the binary exists, is executable and then show all the libraries and whether they are found.

FYI, I compiled the Xbae library and twlog itself from the source - for that, I needed the following packages: **libmotif-dev libmotif3 motif-clients libxp-dev libxpm-dev**.

---

### Post by PaulFr on 2007-06-19
Here's the output from running 'ldd /usr/local/bin/twlog' on my machine:

        linux-gate.so.1 =>  (0xffffe000)
        libXbae.so.4 => /usr/local/lib/libXbae.so.4 (0xb7f10000)
        libXm.so.3 => /usr/lib/libXm.so.3 (0xb7cb6000)
        libXp.so.6 => /usr/lib/libXp.so.6 (0xb7cad000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7c9f000)
        libXt.so.6 => /usr/lib/libXt.so.6 (0xb7c4e000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7b5d000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb7b54000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb7b3c000)
        libXpm.so.4 => /usr/lib/libXpm.so.4 (0xb7b2b000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb79ea000)
        libXmu.so.6 => /usr/lib/libXmu.so.6 (0xb79d4000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb79d1000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb79cc000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb79c7000)
        /lib/ld-linux.so.2 (0xb7f53000)

---

### Post by malel on 2007-06-24
Sorry for the late reply . I have tried that command but there is nothing there so I guess it has not been downloaded by Synaptic. All indications from Synaptic was that it had downloaded it and it was installed . Will keep trying spose. rgds

---

### Post by malel on 2007-06-24
I have located twlog in /usr/share/twlog but there is just an empty folder sitting there. Nothing at all shows up in /usr/local/bin. I remove the folder with 'sudo apt-get remove twlog' and that clears out the folder but when I do 'sudo apt-get install twlog' it tells me that it has installed twlog and two lib's but twlog is certainly not in /usr/share

---

### Post by PaulFr on 2007-06-25
For me, /usr/local/bin was the destination because I was compiling from source. I tried using apt-get install twlog and the main binary is at /usr/bin/twlog. I ran the 'twlog'  binary and did not have a problem in bringing up the GUI. 

FYI, I used the following steps to find out which files have been installed as part of the package,  in Synaptic, just right-click on twlog and select Properties. This will bring up a dialog that has "Installed Files" and it will show the list of installed files.

Please run **ldd /usr/bin/twlog** on your machine. Here's the output on my machine:
        linux-gate.so.1 =>  (0xffffe000)
        libXbae.so.4 => /usr/lib/libXbae.so.4 (0xb7f5c000)
        libXm.so.2 => /usr/lib/libXm.so.2 (0xb7e2e000)
        libXp.so.6 => /usr/lib/libXp.so.6 (0xb7e26000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7e17000)
        libXt.so.6 => /usr/lib/libXt.so.6 (0xb7dc6000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7cd5000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb7ccc000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb7cb4000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b73000)
        libXpm.so.4 => /usr/lib/libXpm.so.4 (0xb7b62000)
        libXft.so.2 => /usr/lib/libXft.so.2 (0xb7b50000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7b48000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7b45000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7b40000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7b3b000)
        /lib/ld-linux.so.2 (0xb7fb7000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb7b10000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7aa5000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7a91000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb7a71000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7a59000)

If you see any library that is 'not found', that means at least one package that twlog needs, is not installed.

---

### Post by PaulFr on 2007-06-25
Ahh, a simpler way to find out the location of the 'twlog' binary is the command: **which twlog** (yet another command to get this is **type twlog**). This will give the path, then you can run 'ldd' on that path.

---

### Post by malel on 2007-06-26
Thank you for your patience . I have managed to locate twlog in /usr/bin/twlog but it will not open or run.This is what I get when I run the which command
mal@Sempron:~$ which twlog
/usr/bin/twlog
mal@Sempron:~$ twlog
Compiled with @(#)GNU/LessTif Version 2.1 Release 0.94.4
Running  with @(#)GNU/LessTif Version 2.1 Release 0.94.4
doing hack for lesstif
twlog: No such file or directory
twlog: Can't find log directory /home/mal/.twlogDir/
mal@Sempron:~$ /usr/bin/twlog
Compiled with @(#)GNU/LessTif Version 2.1 Release 0.94.4
Running  with @(#)GNU/LessTif Version 2.1 Release 0.94.4
doing hack for lesstif
twlog: No such file or directory
twlog: Can't find log directory /home/mal/.twlogDir/
mal@Sempron:~$ 

This is what I get when I run the 'ldd' cmd

mal@Sempron:~$ ldd /usr/bin/twlog
        linux-gate.so.1 =>  (0xffffe000)
        libXbae.so.4 => /usr/lib/libXbae.so.4 (0xb7f10000)
        libXm.so.2 => /usr/lib/libXm.so.2 (0xb7de2000)
        libXp.so.6 => /usr/lib/libXp.so.6 (0xb7dda000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7dcc000)
        libXt.so.6 => /usr/lib/libXt.so.6 (0xb7d7b000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c8a000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb7c80000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb7c68000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b27000)
        libXpm.so.4 => /usr/lib/libXpm.so.4 (0xb7b17000)
        libXft.so.2 => /usr/lib/libXft.so.2 (0xb7b05000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7afd000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7af9000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7af4000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7af0000)
        /lib/ld-linux.so.2 (0xb7f60000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb7ac5000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7a5a000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7a45000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb7a25000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7a0e000)
mal@Sempron:~$ 

In /usr/bin/twlog  there is 54Kb

It seems like I am missing  .twlogDir/

How can I correct that.

Many thanks

---

### Post by PaulFr on 2007-06-27
The ldd output indicates you have all the libraries you need. I checked my home directory and indeed I had an existing directory **.twlogDir** with a number of files in it.

To simulate your problem, I removed that directory completely, and there it was - I got the same error you got. So to fix the problem, I only needed to run the two commands in a terminal : ```
mkdir ~/.twlogDir
touch ~/.twlogDir/logfile
``` and twlog worked again. Please try these out.

---

### Post by malel on 2007-06-27
Brilliant . That worked a treat and I now have 'twlog' up and running . Many thanks for your help 
PaulFr

Kind regards :)

---

