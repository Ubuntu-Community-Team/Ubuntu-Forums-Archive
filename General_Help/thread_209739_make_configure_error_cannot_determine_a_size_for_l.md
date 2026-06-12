---
title: "make configure: error: cannot determine a size for long long"
date: 2006-07-05
forum: General Help
---

### Post by mikewashere05 on 2006-07-05
I've been trying to setup the GNU tool chain for the past three days to no luck, this is my last attempt before I have to go back to Windows for my programming.

I configure binutils fine, but when I sudo make I get the error
"configure: error: cannot determine a size for long long"
and it exits out. I am following the instructions located at [http://www.nongnu.org/avr-libc/user-manual/install_tools.html](http://www.nongnu.org/avr-libc/user-manual/install_tools.html)

Please help me, I really want to keep Ubuntu but I need to program moreso.

---

### Post by mikewashere05 on 2006-07-05
I'm having another problem installing the Synaptics drivers which I think might be related. When I make I get
```

mike@mike-laptop:~/Desktop/synaptics-0.14.5$ make
gcc -O2 -pedantic -Wall -Wpointer-arith -fno-merge-constants -DVERSION="\"0.14.5\""  -DVERSION_ID="(0*10000+14*100+5)" -IXincludes/usr/X11R6/include -c -o synclient.o synclient.c
In file included from synclient.c:22:
/usr/include/sys/types.h:192: error: conflicting types for ‘int16_t’
/usr/local/include/stdint.h:104: error: previous declaration of ‘int16_t’ was here
/usr/include/sys/types.h:193: error: conflicting types for ‘int32_t’
/usr/local/include/stdint.h:120: error: previous declaration of ‘int32_t’ was here
synclient.c: In function ‘set_variables’:
synclient.c:153: warning: implicit declaration of function ‘index’
synclient.c:153: warning: incompatible implicit declaration of built-in function ‘index’
synclient.c:175: warning: implicit declaration of function ‘rint’
synclient.c:175: warning: incompatible implicit declaration of built-in function ‘rint’
synclient.c: In function ‘monitor’:
synclient.c:260: warning: implicit declaration of function ‘fflush’
synclient.c: In function ‘main’:
synclient.c:330: warning: implicit declaration of function ‘perror’
make: *** [synclient.o] Error 1

```

Tonight is my last night to have this figured out, I need to be able to work on my projects tomorrow. So I either have to get this fixed, re-install Ubuntu and see if it works fresh or just switch back to Windows.

Windows is seeming to be the easier choice now :(

---

### Post by tonyr on 2006-07-05
In ubuntu, the way to get the basic compile/build tools is to install the package
**build-essential**.  You can use the GUI tool **Synaptic**,
(**System->Administration->Synaptic Package Manager**) or in a terminal
(Applications->Accessories->Terminal) from the command line
```

sudo apt-get install build-essential

```

---

