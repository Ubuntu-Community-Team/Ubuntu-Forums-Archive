---
title: "How to build 32bit binary on 64bit Ubuntu system with Mono?"
date: 2022-10-23
forum: General Help
---

### Post by diegoboy619 on 2022-10-23
[COLOR=#232629][FONT=-apple-system]Hello I'm trying to build a 32 bit library with Mono on my 64 bit system (Jammy Jellyfish).[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
I'm aware the -platform x 86 flag is for the compiler and has no bearing on the memory space allocated to your program by the mono runtime.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
What's the best way to solve this? I looked into installing 32 bit Mono but I don't know what version of Ubuntu supported that.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
Anyone know how to solve this?

```

[/FONT][/COLOR]tim@ThinkpadTM:~/CLR-DEV9/CLR_DEV9_LINUX_MONO$ ./build.sh
E: Unable to locate package libmonosgen-2.0-1:i386
E: Couldn't find any package by glob 'libmonosgen-2.0-1'
E: Couldn't find any package by regex 'libmonosgen-2.0-1'
E: Unable to locate package libmonosgen-2.0-dev:i386
E: Couldn't find any package by glob 'libmonosgen-2.0-dev'
E: Couldn't find any package by regex 'libmonosgen-2.0-dev'
E: Unable to locate package mono-runtime-common:i386
E: Unable to locate package libgdiplus:i386
Get:1 https://download.mono-project.com/repo/ubuntu stable-focal/main amd64 libmono-corlib4.5-cil all 6.12.0.182-0xamarin1+ubuntu2004b1 [1,261 kB]
Get:2 https://download.mono-project.com/repo/ubuntu stable-focal/main amd64 libmono-system-core4.0-cil all 6.12.0.182-0xamarin1+ubuntu2004b1 [312 kB]
Get:3 https://download.mono-project.com/repo/ubuntu stable-focal/main amd64 libmono-system-drawing4.0-cil all 6.12.0.182-0xamarin1+ubuntu2004b1 [171 kB]
Get:4 https://download.mono-project.com/repo/ubuntu stable-focal/main amd64 libmono-system-management4.0-cil all 6.12.0.182-0xamarin1+ubuntu2004b1 [46.9 kB]
Get:5 https://download.mono-project.com/repo/ubuntu stable-focal/main amd64 libmono-system-runtime-serialization4.0-cil all 6.12.0.182-0xamarin1+ubuntu2004b1 [268 kB]
Get:6 https://download.mono-project.com/repo/ubuntu stable-focal/main amd64 libmono-system-windows-forms4.0-cil all 6.12.0.182-0xamarin1+ubuntu2004b1 [824 kB]
Get:7 https://download.mono-project.com/repo/ubuntu stable-focal/main amd64 libmono-system-xml4.0-cil all 6.12.0.182-0xamarin1+ubuntu2004b1 [825 kB]
Get:8 https://download.mono-project.com/repo/ubuntu stable-focal/main amd64 libmono-system4.0-cil all 6.12.0.182-0xamarin1+ubuntu2004b1 [816 kB]
Fetched 4,523 kB in 1s (4,048 kB/s)            
Get:1 https://download.mono-project.com/repo/ubuntu stable-focal/main amd64 libmono-accessibility4.0-cil all 6.12.0.182-0xamarin1+ubuntu2004b1 [35.9 kB]
Get:2 https://download.mono-project.com/repo/ubuntu stable-focal/main amd64 libmono-i18n-west4.0-cil all 6.12.0.182-0xamarin1+ubuntu2004b1 [47.9 kB]
Get:3 https://download.mono-project.com/repo/ubuntu stable-focal/main amd64 libmono-i18n4.0-cil all 6.12.0.182-0xamarin1+ubuntu2004b1 [42.9 kB]
Get:4 https://download.mono-project.com/repo/ubuntu stable-focal/main amd64 libmono-posix4.0-cil all 6.12.0.182-0xamarin1+ubuntu2004b1 [102 kB]
Get:5 https://download.mono-project.com/repo/ubuntu stable-focal/main amd64 libmono-system-configuration4.0-cil all 6.12.0.182-0xamarin1+ubuntu2004b1 [74.1 kB]
Get:6 https://download.mono-project.com/repo/ubuntu stable-focal/main amd64 libmono-system-servicemodel-internals0.0-cil all 6.12.0.182-0xamarin1+ubuntu2004b1 [101 kB]
Fetched 404 kB in 0s (975 kB/s)                                   
'../CLR_DEV9/bin/Debug/CLR_DEV9.dll' -> 'CLR_DEV9.dll'
-- Configuring done
-- Generating done
-- Build files have been written to: /home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/x86/Debug
/snap/cmake/1156/bin/cmake -S/home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO -B/home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/x86/Debug --check-build-system CMakeFiles/Makefile.cmake 0
/snap/cmake/1156/bin/cmake -E cmake_progress_start /home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/x86/Debug/CMakeFiles /home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/x86/Debug//CMakeFiles/progress.marks
make  -f CMakeFiles/Makefile2 all
make[1]: Entering directory '/home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/x86/Debug'
make  -f CMakeFiles/clrdev9mono.dir/build.make CMakeFiles/clrdev9mono.dir/depend
make[2]: Entering directory '/home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/x86/Debug'
cd /home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/x86/Debug && /snap/cmake/1156/bin/cmake -E cmake_depends "Unix Makefiles" /home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO /home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO /home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/x86/Debug /home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/x86/Debug /home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/x86/Debug/CMakeFiles/clrdev9mono.dir/DependInfo.cmake --color=
Dependencies file "CMakeFiles/clrdev9mono.dir/DEV9.cpp.o.d" is newer than depends file "/home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/x86/Debug/CMakeFiles/clrdev9mono.dir/compiler_depend.internal".
Dependencies file "CMakeFiles/clrdev9mono.dir/PSE.cpp.o.d" is newer than depends file "/home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/x86/Debug/CMakeFiles/clrdev9mono.dir/compiler_depend.internal".
Consolidate compiler generated dependencies of target clrdev9mono
make[2]: Leaving directory '/home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/x86/Debug'
make  -f CMakeFiles/clrdev9mono.dir/build.make CMakeFiles/clrdev9mono.dir/build
make[2]: Entering directory '/home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/x86/Debug'
[ 33%] Linking CXX shared library libclrdev9mono.so
/snap/cmake/1156/bin/cmake -E cmake_link_script CMakeFiles/clrdev9mono.dir/link.txt --verbose=1
/usr/bin/c++ -fPIC -g -shared -Wl,-soname,libclrdev9mono.so -o libclrdev9mono.so CMakeFiles/clrdev9mono.dir/DEV9.cpp.o CMakeFiles/clrdev9mono.dir/PSE.cpp.o "/home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/CLR_DEV9.o"  /usr/lib/libmonosgen-2.0.so -lm -lrt -ldl -lpthread 
/usr/bin/ld: i386 architecture of input file `/home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/CLR_DEV9.o' is incompatible with i386:x86-64 output
collect2: error: ld returned 1 exit status
make[2]: *** [CMakeFiles/clrdev9mono.dir/build.make:116: libclrdev9mono.so] Error 1
make[2]: Leaving directory '/home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/x86/Debug'
make[1]: *** [CMakeFiles/Makefile2:83: CMakeFiles/clrdev9mono.dir/all] Error 2
make[1]: Leaving directory '/home/tim/CLR-DEV9/CLR_DEV9_LINUX_MONO/obj/x86/Debug'
make: *** [Makefile:91: all] Error 2
cp: cannot stat 'obj/x86/Debug/libclrdev9mono.so': No such file or directory


[COLOR=#232629][FONT=-apple-system]
```
[/FONT][/COLOR]

---

