---
title: "Install arm-none-eabi-gcc"
date: 2021-03-11
forum: General Help
---

### Post by janvi2 on 2021-03-11
For several reasons, I like to install the latest version of arm-none-eabi-gcc what is maintained by ARM and downloaded from [U][URL="https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads"]
https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads[/URL][/U]

If I proceed with sudo apt-get always older versions from Ubuntu archive (using Debian packages?) are installed. This is also the installation method recommended in all the many forums. I removed all older versions again and tried to install latest ARM version. Therfore I unpacked the Tarball to any directory what is tmp in this example. Now it is possible to invoke the compiler directly by using ./ before the name:

  >jv@JamesWebb:~/tmp/gcc-arm-none-eabi-10-2020-q4-major/bin$ ./arm-none-eabi-gcc --version

  >arm-none-eabi-gcc (GNU Arm Embedded Toolchain 10-2020-q4-major) 10.2.1 20201103 (release)

 >Copyright (C) 2020 Free Software Foundation, Inc.

 
Probably I only have to set the file to executable and add a valid search path what enables make to find it. Unfortunately using 

 >chmod +x arm-none-eabi-gcc

 will not remove the need of ./ prefix for execution. Why is this, how to set search path and is there another recommended method to install tarball ?

---

### Post by Holger_Gehrke on 2021-03-11
'chmod +x ...' marks a file as executable. Since you could call the compiler by prefixing './' it was already marked that way.

The problem isn't executing the program, finding it is. On Linux systems the current working directory is not searched for programs for security reasons (just imagine someone leaving a script named 'ls' with some bad stuff in it in a directory ...) so you have to explicitly tell the shell to search there - that's what './' means.

There is a variable in the environment named PATH that holds a colon separated list of directories that are searched for executable files. So you have two options. You can move the compiler to a directory that's in PATH. '/usr/local/bin/' would be right for system wide installation of a program that is not installed from a package, for a program that is only supposed to be used by one user there's .local/bin/ in your home directory. Or you can add the directory with the compiler to PATH preferably in the start-up script for the shell (.bashrc in your home directory) by adding a line with 'PATH=$PATH:/path/to/the/compiler/'.

One thing I should probably mention is that files and directories whose name begins with a period - like '.bashrc' or '.local/' - are not shown by 'ls' or by graphical file managers unless you explicitly tell those programs to show them (the '-a' option for ls, the keys 'strg-h' in most file managers).

Holger

---

### Post by janvi2 on 2021-03-14
The apt-get installation seems to go to usr/bin instead usr/local/bin and can be uninstalled by sudo apt-get remove gcc-arm-none-eabi very comfortable to replace it by latest tarball contents.
As Holger had foreseen my next problem, console displays other directory contents than Gnome. As attached screendump shows, cntl H is selected but behaviour seems not limited to files only with names prefixed by a dot. Console ls shows arm-none-eabi executables while Gnome does not.

---

### Post by Holger_Gehrke on 2021-03-14
I don't think nautilus is showing you '**/**usr/bin/' (far to few files, there should be thousands in there). I think that's actually '/media/jv/uuid_of_Datenträger_74MB/usr/bin/'. Try hitting 'ctrl-l' (that's a lower case 'L') to open a location entry field in your file manager and enter '/usr/bin/'. The slash at the beginning is important, without this slash it's a relative path starting at the current working directory with the slash it's an absolute path starting at the root of the filesystem tree. If Gnome's Nautilus behaves anything like XFCE's Thunar using a relative path in a location entry should use the home directory as current working directory.

Mixing files controlled by package management and manually installed files in the same directories is a recipe for confusion IMHO.  When looking for executables the directories in PATH are searched in the order given in PATH, so programs in /usr/local/bin would be found and executed without even looking at /usr/bin. That way you can have both the package managed version and a manually installed version of the same program and select which one to use by giving the path to the executable (or not).

Holger

---

### Post by janvi2 on 2021-03-14
You are correct. Nautilus shown a complete diffrent usr/bin instead expected /usr/bin. The identical selection here with Nautilus is Rechner - usr - bin. Even the searched /usr/local/bin appears now correct in Nautilus. Moving the executables to /usr/local/bin works and they prevail over older version. Nevertheless there seems other components, mainly the runtime lib what constists of gcc version dependent libgcc (beside executable parts as cc1) and targed dependent newlib parts who all seems to go to /usr/lib/gcc/arm-none-eabi/.... Doing these copies manually cannot link them by invoking gcc and usr/lib seems not to have default path links to gcc like /usr/bin/ or /usr/local/bin have for execution. Probably we must not touch the tarball directory structure until we build gcc from source. 

After creating a symbol link into /usr/local/bin, my target projects compile well and the tarball directory structure can be stored in ~/AnyOtherDirectoryOfChoice. A benefit of invoking the linker ld indirect by gcc (instead direct in makefile) is, that there is only one symbol link to the gcc executable required. Older gcc versions installed by apt-get can reside in parallel as they have alias copy named arm-none-eabi-gcc-version. Also no further path instructions in linker script are required to find the runtime archives inside the tarball dir tree.

---

