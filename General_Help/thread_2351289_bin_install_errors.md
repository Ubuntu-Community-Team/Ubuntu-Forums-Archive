---
title: "bin install errors"
date: 2017-02-01
forum: General Help
---

### Post by cmcanulty on 2017-02-01
I am trying to install a .bin file that we need for the library software and am getting an error. It is marked executable. I am wondering if this is caused by having oracle-java8 as the default which I had to do to make minecraftedu we use at the library install correctly. Or maybe some other missing app? I couldn't find libc.so.6 in synaptic. Here is the terminal error.

I tried this fix already  

```
sudo ln -s /lib64/x86_64-linux-gnu/libc.so.6 /lib64/libc.so.6
```


```
librarian@Ubuntu3:~$ ./milup160_02.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...

Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
strings: '/lib/libc.so.6': No such file

Launching installer...

Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.UnsatisfiedLinkError: /tmp/install.dir.6127/Linux/resource/jre/lib/i386/xawt/libmawt.so: libXtst.so.6: cannot open shared object file: No such file or directory
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1647)
	at java.lang.Runtime.load0(Runtime.java:770)
	at java.lang.System.load(System.java:1005)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.awt.NativeLibLoader.loadLibraries(NativeLibLoader.java:38)
	at sun.awt.DebugHelper.<clinit>(DebugHelper.java:29)
	at java.awt.Component.<clinit>(Component.java:552)
	at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
	at com.zerog.ia.installer.LifeCycleManager.h(DashoA8113)
	at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
	at com.zerog.ia.installer.Main.main(DashoA8113)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.zerog.lax.LAX.launch(DashoA8113)
	at com.zerog.lax.LAX.main(DashoA8113)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)
librarian@Ubuntu3:~$ 
```

thank you

---

### Post by TheFu on 2017-02-01
"bin" doesn't tell anyone anything. It is a generic extension that could be for anything. Could be a script, compiled, or data. Usually it is an input to a "install" or "setup" file which makes local environment changes for the installation. It would be odd to run any .bin file directly, IME.  So, my only suggestion is that you follow the installation instructions that came with the entire package from the same software provider.  If there aren't any instructions, complain to them.

BTW, I hope that symbolic link didn't break anything else.  It is a bad idea to run commands without a good understanding of what they actually do.  Plus, it is important to recognize when a blogger who thinks they've just came up with a solution by "typing these exact commands and it worked for me" really hasn't got a clue.  I see bad advice given on blogs all the time.

---

### Post by cmcanulty on 2017-02-01
OK I was given from the mid michigan library league and told it is the install file for the software on linux, no help files for linux
How would I undo the command below

sudo ln -s /lib64/x86_64-linux-gnu/libc.so.6 /lib64/libc.so.6

---

### Post by deadflowr on 2017-02-01
Should be
```
sudo unlink /lib64/libc.so.6
```

---

### Post by cmcanulty on 2017-02-02
OK thanks now I just have to get this done soon as the librarian needs the program.

---

### Post by steeldriver on 2017-02-02
What it actually seems to be complaining about is missing libXtst.so - is the libxtst6 package installed?

---

### Post by cmcanulty on 2017-02-02
synaptic doesn't show that pkg, I am running xubuntu 16.04. I can install it as a windows 98 only under wine (it is very old and needs 32 bit wine setting hence the windows 98). But then it seems to run and install OK until there is a typo then it crashes. There are always lots of typos as the librarians are constantly typing 16 digit barcodes. So I am trying again the linux install and still get the error-

configuring the installer for this system's environment strings: '/lib/libc.so.6' No such file

---

### Post by TheFu on 2017-02-02
> **cmcanulty said:**
> OK I was given from the mid michigan library league and told it is the install file for the software on linux, no help files for linux
How would I undo the command below

Perhaps they didn't give you all the files?  Librarians don't always know things we'd expect, but they are usually completely brilliant in many, unexpected, things. ;)   Used to work with professional librarians at NASA - smart, smart, folks.

---

### Post by steeldriver on 2017-02-02
> **cmcanulty said:**
> synaptic doesn't show that pkg, I am running xubuntu 16.04

[http://packages.ubuntu.com/search?keywords=libxtst6&searchon=names&suite=xenial&section=all](http://packages.ubuntu.com/search?keywords=libxtst6&searchon=names&suite=xenial&section=all)

---

### Post by cmcanulty on 2017-02-02
I just tried to post a very long explanation and I getting not posted because a security code is missing. I put code tags around the 2 sections of code. One section is a bin file, is there another way I should enclose that than code?

---

### Post by wildmanne39 on 2017-02-02
Close the tab that you were try to type in and open a new one some times that helps, we are having some forum issues that probably caused the problem.

---

### Post by cmcanulty on 2017-02-02
Still same error 

Your submission could not be processed because a security token was missing. Is there another wat to send it I saved the post as a txt file.

---

### Post by wildmanne39 on 2017-02-02
I suggest waiting a few minutes and trying again, or you can hit the refresh button and reload the page that usually refreshes the token.

---

### Post by cmcanulty on 2017-02-02
Still getting missing security token. Is there another way to post it? reload doesn't work. I will try it in 2 sections.

---

### Post by wildmanne39 on 2017-02-02
Not that I know of.

---

### Post by cmcanulty on 2017-02-02
OK I gave up on wine it seems to install and run but crashes too much. Here is the terminal output that shows the missing file but then I did locate and the file is there

```
librarian@Ubuntu3:~$ ./milup160_03.bin
bash: ./milup160_03.bin: No such file or directory
librarian@Ubuntu3:~$ ./milup160_02.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
strings: '/lib/libc.so.6': No such file

Launching installer...

librarian@Ubuntu3:~$ locate libc.so.6
/lib/i386-linux-gnu/libc.so.6
/lib/x86_64-linux-gnu/libc.so.6
/lib32/libc.so.6
/lib64/libc.so.6
librarian@Ubuntu3:~$ 

```


OK the contents of the bin file which is the important part won't go even with code tags maybe it is too large at 62MB

I can post the website but I need to give out a name and password for the download, is that OK?

---

### Post by cmcanulty on 2017-02-02
Ok I got it installed and working on 5 computers. I opened port 2000 and that worked. But I am still getting an error on 5 others and I sure can't figure what I've missed on them. Here is the output.


```

librarian@Ubuntu2:~$ ./milup160_02.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
strings: '/lib/libc.so.6': No such file

Launching installer...

Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.UnsatisfiedLinkError: /tmp/install.dir.6078/Linux/resource/jre/lib/i386/xawt/libmawt.so: libXtst.so.6: cannot open shared object file: No such file or directory
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1647)
	at java.lang.Runtime.load0(Runtime.java:770)
	at java.lang.System.load(System.java:1005)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.awt.NativeLibLoader.loadLibraries(NativeLibLoader.java:38)
	at sun.awt.DebugHelper.<clinit>(DebugHelper.java:29)
	at java.awt.Component.<clinit>(Component.java:552)
	at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
	at com.zerog.ia.installer.LifeCycleManager.h(DashoA8113)
	at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
	at com.zerog.ia.installer.Main.main(DashoA8113)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.zerog.lax.LAX.launch(DashoA8113)
	at com.zerog.lax.LAX.main(DashoA8113)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)
librarian@Ubuntu2:~$ 
```

but the file is there see below

```
librarian@Ubuntu2:~$ locate libc.so.6
/lib/i386-linux-gnu/libc.so.6
/lib/x86_64-linux-gnu/libc.so.6
/lib32/libc.so.6
librarian@Ubuntu2:~$ 
```

---

### Post by cmcanulty on 2017-02-02
finally got the all by adding the repository for libxtst6:i386 then installing libxtst6:i386 with apt, then update upgrade and it finally works and even looks good
but I never would have gotten it except for the hint on libxtst6:i386 as the error was saying a different file was missing. Thanks all !!!

---

