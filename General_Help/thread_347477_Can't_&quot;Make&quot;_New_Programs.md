---
title: "Can't &quot;Make&quot; New Programs"
date: 2007-01-27
forum: General Help
---

### Post by Sleepy_Sentry on 2007-01-27
I'm trying to install ndiswrapper 1.34 that I downloaded from the ndiswrapper website. I am using a fresh install Ubuntu Edgy Eft 6.10.

Upon trying to make ndiswrapper, I got these errors.

The latest Linux headers are installed. I did some research and found this error was caused by the lack of libc6-dev package. However, all the libc6 packages available in Synaptics are already installed.

How can I fix this?

```

daniel@daniel-desktop:~$ cd /home/daniel/ndiswrapper-1.34/
daniel@daniel-desktop:~/ndiswrapper-1.34$ sudo make
make -C driver
make[1]: Entering directory `/home/daniel/ndiswrapper-1.34/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/daniel/ndiswrapper-1.34/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/home/daniel/ndiswrapper-1.34/driver'
make -C utils
make[1]: Entering directory `/home/daniel/ndiswrapper-1.34/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:179: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:179: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:183: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:195: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:206: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:218: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:218: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:220: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:222: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:223: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:225: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:231: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:233: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:233: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:233: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:250: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:250: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:252: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:256: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:256: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:258: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:260: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:262: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:268: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:268: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:272: warning: implicit declaration of function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:273: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:281: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:281: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:283: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:285: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘stat’
loadndisdriver.c:288: error: dereferencing pointer to incomplete type
loadndisdriver.c:289: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:295: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:295: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:300: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:304: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:314: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:319: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:322: error: dereferencing pointer to incomplete type
loadndisdriver.c:283: warning: unused variable ‘statbuf’
loadndisdriver.c:345: error: expected expression before ‘struct’
loadndisdriver.c:347: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:349: warning: implicit declaration of function ‘free’
loadndisdriver.c:356: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:356: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:356: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:368: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:371: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:371: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:375: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:377: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:377: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:408: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:368: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:420: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:420: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:424: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:424: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:425: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:427: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:428: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:430: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:435: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:437: error: dereferencing pointer to incomplete type
loadndisdriver.c:440: error: dereferencing pointer to incomplete type
loadndisdriver.c:449: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:466: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:466: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:474: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:474: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:475: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:475: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:485: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:485: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:490: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:491: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:491: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:491: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:492: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:497: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:513: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:513: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:515: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:517: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:519: warning: implicit declaration of function ‘printf’
loadndisdriver.c:519: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:529: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:544: warning: implicit declaration of function ‘atof’
loadndisdriver.c:551: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:558: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:592: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/daniel/ndiswrapper-1.34/utils'
make: *** [all] Error 2
daniel@daniel-desktop:~/ndiswrapper-1.34$ 

```

---

### Post by jpeddicord on 2007-01-27
It almost looks as if the linux-headers-generic package is not installed. Check to see if it is, that may fix your problem.

---

### Post by dexter on 2007-01-27
Why don't you install it from the repo's ?

---

### Post by Sleepy_Sentry on 2007-01-27
Linux-headers-generic is installed.

I am trying to download libc6-dev from the repository using this page.
[http://packages.ubuntu.com/edgy/libdevel/libc6-dev](http://packages.ubuntu.com/edgy/libdevel/libc6-dev)

However, none of the i386 file links work on my Windows PC. I can't download anything on my Ubuntu box because I need ndis-wrapper to get Internet. I also couldn't find ndis wrapper in the repository, if that's what you meant by " Why don't you install it from the repo's ?" dexter.

---

### Post by phossal on 2007-01-27
You can install ndiswrapper from the live cd. You did install from a cd, right? To "find it" in the repos,

```
sudo apt-get install  ndiswrapper-utils-1.8
```

Now you have two ways without having to "make" it yourself. ;)

---

### Post by Sleepy_Sentry on 2007-01-27
> **phossal said:**
> You can install ndiswrapper from the live cd. You did install from a cd, right?

I'll try that out.

I'm not the only one having the same problem, either.
[http://ubuntuforums.org/showthread.php?t=346477](http://ubuntuforums.org/showthread.php?t=346477)

---

### Post by phossal on 2007-01-27
[Install from the live cd]("http://ubuntuforums.org/showthread.php?t=335853#2")

---

### Post by Sleepy_Sentry on 2007-01-27
It looks like it worked! Thanks!

---

### Post by phossal on 2007-01-27
Yeah, you're welcome. I caution you though, about confusing it with the *other* problem. Most wireless hardware will work using the available version of ndiswrapper - 1.8. However, a lot of tutorials recommend using a later version because of added support for various new drivers. While it's likely your hardware will work using 1.8, for those who truly *need* 1.34, they're still going to face the problem of linking in the headers (which are also available via apt-get).

---

### Post by chalupa on 2007-01-27
> **phossal said:**
> Yeah, you're welcome. I caution you though, about confusing it with the *other* problem. Most wireless hardware will work using the available version of ndiswrapper - 1.8. However, a lot of tutorials recommend using a later version because of added support for various new drivers. While it's likely your hardware will work using 1.8, for those who truly *need* 1.34, they're still going to face the problem of linking in the headers (which are also available via apt-get).

I am not at my place right now, but as soon as I get there i will install ndsiwrapper from the live cd. However, the reason i did not do that in the first place is for two reasons:

1) reading through the forums it appeared as though the ndiswrapper on the live cd was broken

2) everyone that has posted their success with my mobo (asus p5w dh deluxe) has said that they had to install ndsiwrapper from scratch by downloading it from ndiswrapper's website then use old windows 98 drivers... so hopefully 1.8 will still work with my motherboards onboard wireless.

Just in case it doesn't work, does anyone know how to fix this problem with gcc not being able to find all of those .h files?

---

### Post by chalupa on 2007-01-27
Alright i installed ndiswrapper from the ubuntu install cd and then installed the windows 98 driver for the on board wireless for my asus p5w dh deluxe. It didn't work. I read through the forums again and everywhere i see a success story it has this ending:

installed ndiswrapper 1.24/1.33/1.34, etc from source.
installed windows 98 drivers
works fine!!

i hate having to use windows just to get online.... if anyone knows how to get make to work when trying to install ndiswrapper 1.34 from source PLEASE help!

iwlist wlan0 scan finds the network, but i just cannot connect to it. It seems the only solution involves installing ndiswrapper manually, which i cannot do :(

thank you in advance!

---

### Post by phossal on 2007-01-27
I actually upgraded ndiswrapper today, just to see if I could help you. Let's walk through the steps together. First, what version of Ubuntu are you using? 64 or 32 Bit?

---

### Post by chalupa on 2007-01-27
thank you! :D 

32 bit.

note: I cannot access internet through ubuntu, but i can download any necessary files onto my hd via windows and access them on ubuntu

---

### Post by phossal on 2007-01-27
Step 1. [Download ndiswrapper]("http://sourceforge.net/project/showfiles.php?group_id=93482"). I realize you've already done this, but let's do it again. So, get the file. Download it to your desktop.

Extract it according to the directions: once downloaded, you're going to cd to your Desktop, and issue this command: ```
tar zxvf ndiswrapper-version.tar.gz
```

That will give you a file on your desktop named: ndiswrapper-1.34

---

### Post by chalupa on 2007-01-27
alright, im in the ndiswrapper-1.34 directory i just extracted. I won't do anything yet, but should i do make uninstall?

note: I am connected to the Internet on my laptop and sitting in front of the desktop computer

---

### Post by phossal on 2007-01-27
lol Trust me. It's important that you extract it the *right* way. Assuming you did, yes, run:
```
sudo make uninstall
```
And run it about 5 times. lol (I'm including lol's because I'm laughing, but I'm not necessarily *kidding*) Run it about 5 times.

---

### Post by phossal on 2007-01-27
Then...
```
sudo make
```

---

### Post by chalupa on 2007-01-27
Alright, i got three remove messages.... should i repeat until there are no more?

By the way, thank you so much for this!

---

### Post by phossal on 2007-01-27
The output to sudo make looks like this:

```
bash 3.1:**sudo make**
make -C driver
make[1]: Entering directory `/home/phossal/Desktop/ndiswrapper-1.34/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/phossal/Desktop/ndiswrapper-1.34/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  LD      /home/phossal/Desktop/ndiswrapper-1.34/driver/built-in.o
  CC [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/crt.o
  CC [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/hal.o
  CC [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/iw_ndis.o
  CC [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/loader.o
  CC [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/ndis.o
  CC [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/ntoskernel.o
  CC [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/ntoskernel_io.o
  CC [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/pe_linker.o
  CC [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/pnp.o
  CC [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/proc.o
  CC [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/rtl.o
  CC [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/wrapmem.o
  CC [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/wrapndis.o
  CC [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/wrapper.o
  CC [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/usb.o
  CC [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/divdi3.o
  LD [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /home/phossal/Desktop/ndiswrapper-1.34/driver/ndiswrapper.mod.o
  LD [M]  /home/phossal/Desktop/ndiswrapper-1.34/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/home/phossal/Desktop/ndiswrapper-1.34/driver'
make -C utils
make[1]: Entering directory `/home/phossal/Desktop/ndiswrapper-1.34/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/phossal/Desktop/ndiswrapper-1.34/utils'
```

---

### Post by chalupa on 2007-01-27
ah sorry, missed that. Ok, i sudo make uninstall many many times. Now, when i do sudo make, i still get the same errors: that .h files such as stdio, stdlib, string, etc cannot be found

---

### Post by phossal on 2007-01-27
> **chalupa said:**
> Alright, i got three remove messages.... should i repeat until there are no more? By the way, thank you so much for this!

You're welcome. It was a good process for me, because I was able to upgrade too. We help each other. Anyway, 5 times should be enough. I get a couple error messages when I run it, but I ignore them.

---

### Post by chalupa on 2007-01-27
i have the same problem as the OP. When make gets to this command: gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c

it cannot find all of those .h files that pretty much every C program includes.

---

### Post by phossal on 2007-01-27
You don't have cat 5 to the machine in question? You can't use apt-get, etc?

---

### Post by chalupa on 2007-01-27
I dont understand your question... i can do apt-get, just i cannot connect to the internet. By cat 5 do you mean can i run the command "cat [file]"? Sorry i am pretty new to linux

---

### Post by phossal on 2007-01-27
What happens when you run this:
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by chalupa on 2007-01-27
ah lol sorry cat 5 the cable...no the problem is that the router is in another room in the house and there is no cable long enough to reach to my room.

---

### Post by chalupa on 2007-01-27
> **phossal said:**
> What happens when you run this:
```
sudo apt-get install linux-headers-`uname -r`
```

What do i replace with uname -r? Sorry for all this trouble

Edit: just remembered, one of my roommates uses x-box live and runs it directly to the router with a long ethernet cable... ill go see if its long enough to reach my room

---

### Post by phossal on 2007-01-27
Nothing. You run that command the way it is.

---

### Post by chalupa on 2007-01-27
It returns:

Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-headers-2.6.17-10-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Good news: i just got the ethernat cord from the x box and wow its much longer than i thought, so i actually can get internet access if necessary to solve this problem

---

### Post by phossal on 2007-01-27
Good. And what happens when you run:
```
sudo apt-get install build-essential
```

---

### Post by chalupa on 2007-01-27
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6162kB of archives.
After unpacking 25.1MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package libc6-dev.
(Reading database ... 88903 files and directories currently installed.)
Unpacking libc6-dev (from .../libc6-dev_2.4-1ubuntu12_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.1-13ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.1-6ubuntu3_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.22ubuntu7_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Setting up libc6-dev (2.4-1ubuntu12) ...
Setting up dpkg-dev (1.13.22ubuntu7) ...
Setting up libstdc++6-4.1-dev (4.1.1-13ubuntu5) ...
Setting up g++-4.1 (4.1.1-13ubuntu5) ...
Setting up g++ (4.1.1-6ubuntu3) ...

Setting up build-essential (11.3) ...



All seems good... should i try make again?

then make install?

do i need to reinstall the driver i installed with previous version of ndiswrapper?

---

### Post by phossal on 2007-01-27
Try **sudo make** again.

---

### Post by phossal on 2007-01-27
> **chalupa said:**
> 

All seems good... should i try make again? **Yes!**
then make install? **If no errors to sudo make**

do i need to reinstall the driver i installed with previous version of ndiswrapper? **No, I didn't** 

See answers above.

[edit] For the sake of doing it right, yes, you should reinstall the drivers. I didn't stop to think that I already had a working version when I ignored that step. You  might not get so lucky.

---

### Post by chalupa on 2007-01-27
Ding! I also went ahead and sudo make install... and it answered my own question... i have to reinstall any windows drivers. I will do that really quickly and let you know how it goes.

Once again, thank you so much for your help and patience!

---

### Post by phossal on 2007-01-27
If **sudo make install** worked, you should immediately be able to run: ndiswrapper -v

```
bash 3.1:**ndiswrapper -v**
utils version: 1.9
driver version:        1.34
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
bash 3.1:
```

If that works, it's installed!

---

### Post by chalupa on 2007-01-27
Yes thank you so much again!!!

---

### Post by phossal on 2007-01-27
You're welcome, mate. ;) Have a good day/evening!

---

