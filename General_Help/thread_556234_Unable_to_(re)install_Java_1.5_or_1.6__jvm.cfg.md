---
title: "Unable to (re)install Java 1.5 or 1.6 / jvm.cfg"
date: 2007-09-21
forum: General Help
---

### Post by mivo on 2007-09-21
I recently set up a fresh Kubuntu 7.04 system. For a Java application I had to install Java on the system. I don't recall what package I selected, but it turned out to be 1.4. The application did not play sounds. So, I installed sun-java6-sdk, and my sound worked. However, the cache viewer of the Web Starter did not allow me to create a shortcut of the application. I dug around and found some references to this happening if an old shortcut for the Java application already exists. I found none. So I tried Java 1.5, with the same result. Several hours later, I removed both 1.5 and 1.6 and cleaned up manually everything that was related to it. This may have turned out to be a fatal error.

After this, I tried to reinstall 1.5. I used Apitude for this, though trying it with Adept had the same result. The install always fails at the installation of sun-java5-bin (or 6). This is the error message:

```

Setting up sun-java5-bin (1.5.0-11-1ubuntu2) ...
Error: could not open `/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/lib/i386/jvm.cfg'
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java5-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up sun-java5-bin (1.5.0-11-1ubuntu2) ...
Error: could not open `/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/lib/i386/jvm.cfg'
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java5-bin
Press return to continue.

```

The file, /usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/lib/i386/jvm.cfg, does exist, but it is a link to /etc/java-1.5.0-sun/jvm.cfg, which does not exist. I tried re-downloading the packages, and I tried the SDK ones instead of the JRE packages, but the result is always the same. Same with 1.6, just replace 5 with 6 in the error message. I have the sinking feeling that I deleted something I should not have deleted when I cleaned up.

Any ideas what I could try, besides reinstalling the OS? I just finished configuring it after two days, and I would prefer not having to do that again. :(

---

### Post by mivo on 2007-09-21
I've tried a number of ways to purge, remove, reconfigure, etc. the Java installation, but when nothing worked and the same error message came up, I reinstalled Kubuntu. This was quick and painless (/home had its own partition), and after that installing the 1.5 JRE worked flawlessly. I still was not offered the option to make a shortcut of the Java application, so the solution can probably be found somewhere in my /home partition. I made a link manually.

---

### Post by kailas_jc on 2008-06-10
I was also facing the same problem
I was trying to install java 6 using the exe available and after that i tried to uninstall.I was facing the same issue

Even if you set the path the classpath properly in envirinment variables it might not work

There are two ways of solcing this problem
1) to set the path and classpath variable in command prompt and start eclipse from the same command prompt

2)There will be three exe files in the location C:\WINDOWS\system32\.They are java.exe,javaw.exe,javaws.exe.Delete those and start eclipse normally

It is working for me      

It can be 
that

---

