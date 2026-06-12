---
title: "executing libreoffice-dev examples"
date: 2018-08-02
forum: General Help
---

### Post by mastupristi on 2018-08-02
I have installed the libreoffice-dev* packages

then I run setsdkenv_unix
```
max@resfw04:~$ /usr/lib/libreoffice/sdk/setsdkenv_unix

 ************************************************************************
 *
 *  You have to configure your SDK environment first before you can
 *  use it. The configuration has to be done only once.
 *
 ************************************************************************

 Enter the Office installation directory [/usr/lib/libreoffice]: 
 Enter GNU make (3.79.1 or higher) tools directory [/usr/bin]: 
 Enter zip (2.3 or higher) tool directory [/usr/bin]: 
 Enter cat tool directory [/bin]: 
 Enter sed tool directory [/bin]: 
 C++ compilers where for example a language binding exist:
  - Solaris, Sun WorkShop 6 update 1 C++ 5.2 2000/09/11 or higher
  - Linux, GNU C++ compiler, gcc version 4.0.1 or higher
  - MacOS, GNU C++ compiler, gcc version 4.0.1 or higher
 Enter the directory of the C++ compiler, the directory
 where the compiler is located (optional) [/usr/bin]: 
 Enter Java SDK (1.5, recommendation is 1.6 or higher) installation directory  (optional) []: 
 Default output directory is in your HOME directory.
 Enter an existent directory if you prefer a different output directory (optional) [/home/max]: 
 Automatic deployment of UNO components (YES/NO) [YES]: 

 ************************************************************************
 * ... your SDK environment has been prepared.
 * For each time you want to use this configured SDK environment, you
 * have to run the "setsdkenv_unix" script file!
 * Alternatively can you source one of the scripts
 *   "/home/max/libreoffice6.0_sdk/resfw04/setsdkenv_unix.sh"
 * to get an environment without starting a new shell.
 ************************************************************************


 ************************************************************************
 *
 * SDK environment is prepared for Linux
 *
 * SDK = /usr/lib/libreoffice/sdk
 * Office = /usr/lib/libreoffice
 * Make = /usr/bin
 * Zip = /usr/bin
 * cat = /bin
 * sed = /bin
 * C++ Compiler = /usr/bin
 * Java = 
 * SDK Output directory = /home/max/libreoffice6.0_sdk
 * Auto deployment = YES
 *
 ************************************************************************

```

the I compile a cpp example
```
max@resfw04:~$ make -C /usr/lib/libreoffice/sdk/examples/cpp/DocumentLoader/
make: Entering directory '/usr/lib/libreoffice/sdk/examples/cpp/DocumentLoader'
mkdir -p /home/max/libreoffice6.0_sdk/LINUXexample.out/misc
rm -f /home/max/libreoffice6.0_sdk/LINUXexample.out/misc/oosdk_cpp_types.flag
"/usr/lib/libreoffice/sdk/bin/cppumaker" -Gc -O/home/max/libreoffice6.0_sdk/LINUXexample.out/inc "/usr/lib/libreoffice/program/types.rdb" "/usr/lib/libreoffice/program/types/offapi.rdb"
echo flagged > /home/max/libreoffice6.0_sdk/LINUXexample.out/misc/oosdk_cpp_types.flag
mkdir -p /home/max/libreoffice6.0_sdk/LINUXexample.out/obj/DocumentLoader
gcc -c -fpic -fvisibility=hidden -O -I. -I/home/max/libreoffice6.0_sdk/LINUXexample.out/inc -I/home/max/libreoffice6.0_sdk/LINUXexample.out/inc/examples -I../../../include -I/home/max/libreoffice6.0_sdk/LINUXexample.out/inc/DocumentLoader -DUNX -DGCC -DLINUX -DCPPU_ENV=gcc3 -o/home/max/libreoffice6.0_sdk/LINUXexample.out/obj/DocumentLoader/DocumentLoader.o DocumentLoader.cxx
mkdir -p /home/max/libreoffice6.0_sdk/LINUXexample.out/bin
mkdir -p /home/max/libreoffice6.0_sdk/LINUXexample.out/misc/DocumentLoader
g++ -Wl,--allow-shlib-undefined -Wl,-export-dynamic -Wl,-z,defs -Wl,--no-whole-archive -L"/home/max/libreoffice6.0_sdk/LINUXexample.out/lib" -L"/usr/lib/libreoffice/sdk/lib" -L"/usr/lib/libreoffice/program" -o /home/max/libreoffice6.0_sdk/LINUXexample.out/bin/DocumentLoader /home/max/libreoffice6.0_sdk/LINUXexample.out/obj/DocumentLoader/DocumentLoader.o \
  -luno_cppuhelpergcc3 -luno_cppu -luno_salhelpergcc3 -luno_sal 
--------------------------------------------------------------------------------
The example loads the "test.odt" document in the DocumentLoader example directory.
If you want to load your own document, please use:
  DocumentLoader -env:URE_MORE_TYPES="<fileurl_office_types_rdb>" "filename" [connection_url]
-
Use the following command to execute the example!
-
make DocumentLoader.run
-
NOTE: This example does not use the new UNO bootstrap mechanism, it uses still a socket
      connection. The example use the defaultBootstrap_InitialComponentContext method and provides
      the additional office types via the UNO environment variable -env:URE_MORE_TYPES=...
      Before you can run this example you have to start your office in listening mode.
-
  soffice "--accept=socket,host=localhost,port=2083;urp;StarOffice.ServiceManager"
--------------------------------------------------------------------------------
make: Leaving directory '/usr/lib/libreoffice/sdk/examples/cpp/DocumentLoader'

```

Then I run soffice as requested
```
max@resfw04:~$ soffice "--accept=socket,host=localhost,port=2083;urp;StarOffice.ServiceManager" &

```

finally I run the example:
```
max@resfw04:~$ ./libreoffice6.0_sdk/LINUXexample.out/bin/DocumentLoader -env:URE_MORE_TYPES="file:///usr/lib/libreoffice/program/types/offapi.rdb" "file:///usr/lib/libreoffice/sdk/examples/cpp/DocumentLoader/test.odt" "uno:socket,host=localhost,port=2083;urp;StarOffice.ServiceManager" 
terminate called after throwing an instance of 'com::sun::star::lang::IllegalArgumentException'
Aborted (core dumped)

```

It fails

where am I wrong?

best regards
Max

---

### Post by rell2000 on 2018-12-29
Did you find solution?

---

