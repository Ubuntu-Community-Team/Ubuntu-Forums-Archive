---
title: "How does libraries work in ubuntu?"
date: 2022-10-27
forum: General Help
---

### Post by Sceiron on 2022-10-27
Hi all, i have installed libpqxx v6.4 following this guide: [https://github.com/jtv/libpqxx](https://github.com/jtv/libpqxx)

After compiling (.configure/make/make install) my libraries exists in the folder /usr/local/lib
-rw-r--r-- 1 user user  16105016 Oct 24 20:32 libpqxx.a
-rwxr-xr-x 1 user user       885 Oct 24 20:32 libpqxx.la

As i understand it .a is a staic library
and .la is a textual file that includes a description of the library. 

     1. Does that mean a description of the libpqxx.a file?

Further more, as mentioned i installed v6.4 which is old, and i now want to use 7.6 version. 

     2. Can i just delete these two library-files, and recompile a newer version since they are static libraries?

brg
S

---

### Post by Impavidus on 2022-10-27
Normally, we install libraries from the repositories. In this case, use the package libpqxx-6.4. Probably you actually want the dev version of the package, libpqxx-dev, which has the header files and automatically pulls in the actual library as a dependency. If you want to compile something yourself, you need the header files; if you install something from the repos that needs the library, it's pulled in automatically.

libpqxx 6.4 was already used in Ubuntu 20.04. I don't know why it hasn't been updated in such a long time. If you want a more recent version, maybe you can install it from a PPA. Last resort is to download the source code and compile it yourself. For statically linked libraries, which get copied into the executable when you link it, you can replace the library file and relink the applications that you build with them. If the binary interface has changed, also recompile them. For dynamically linked libraries, the new version gets used automatically, provided the (major) version number and binary interface matches. You can have two versions of a library installed at the same time.

/usr/local/lib is the appropriate place to install such manually compiled libraries.

---

### Post by Sceiron on 2022-10-27
OK, full picture:
I got a BeagleBoneBlack that runs debian 10 (buster). Running "sudo apt search libpqxx" returns: libpqxx-dev/oldstable 6.2.5-1 armhf
I dint know it was available in package-repos so thanks!

Anyway, i want to continue on my path:
I deleted the files in /usr/local/lib and recompiled from source with V7.6 and installation seems to be success. But now when i want to compile my own c++App: "task.cpp" (with code from example on that site), i get compiler errors stating:

In function &#8216;int main()&#8217;:
task.cpp:20:43: error: &#8216;using work = class pqxx::transaction<>&#8217; {aka &#8216;class pqxx::transaction<>&#8217;} has no member named &#8216;query&#8217;
             for (auto [name, salary] : tx.query<std::string, int>(
                                           ^~~~~
task.cpp:20:60: error: expected primary-expression before &#8216;,&#8217; token
             for (auto [name, salary] : tx.query<std::string, int>(
                                                            ^
task.cpp:20:62: error: expected primary-expression before &#8216;int&#8217;


Does this mean i miss some header-files containing the mention classes with these methods?
Please help me understand, i have struggeled so long with this issue...

---

### Post by Impavidus on 2022-10-27
Those are compiler errors, not link errors. Either the header file wasn't properly included, or the compiler finds the wrong version of the header file. When you manually install some library to compile stuff, you should get the proper version of the header files and put them in /usr/local/include, then tell the compiler to use header files from that directory before looking in other directories. Although that may actually be the default.

---

### Post by Sceiron on 2022-10-28
Thanks again, helped me in the correct direction. Instead of using the "code-example" from github page, i used the examples from [https://libpqxx.readthedocs.io/en/stable/a01433.html](https://libpqxx.readthedocs.io/en/stable/a01433.html), getting started section. And the classes/methods are named in a different way here. And its working, and like you said the class-names are now probably matching with some header files the library i'm using :D

---

