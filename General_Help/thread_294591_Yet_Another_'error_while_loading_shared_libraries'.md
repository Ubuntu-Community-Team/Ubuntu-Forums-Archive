---
title: "Yet Another 'error while loading shared libraries' thread"
date: 2006-11-06
forum: General Help
---

### Post by Chireru on 2006-11-06
A search brings up a pile of threads with the same problem, but none of them have a solution..

I'm trying to install GalleryRemote (gallery.sf.net) on Edgy, and get this error:

```
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/opt/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
```

Each one of the libraries referenced exists in /lib, ldconfig does see it.

Strace shows it's lying about not being able to open libpthread.so.0, but it doesn't give me much info about the rest..
```
open("/lib/libpthread.so.0", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240J\0"..., 512) = 512
close(3)  
```

Any ideas?

---

### Post by po0f on 2006-11-06
Chireru,

Could you post the command that returned those errors?

---

### Post by Chireru on 2006-11-06
The installer does it...
```
~$ Downloads/GalleryRemote.1.5.Linux.NoVM.bin
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/usr/bin/perl: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
```

And I backed up my home directory, which had a few user-level installed programs, including the Gallery, so my previous install of it also does it:

```
~$ Programs/GalleryRemote/Gallery_Remote
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/opt/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
```

And I even tried the installer with the inline Java to see whether or not it's just my java install, but it does it too...
```
~$ Downloads/GalleryRemote.1.5.Linux.VM.bin 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.19233/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
```

---

### Post by remarks on 2006-11-14
```
cp GalleryRemote.1.5.Linux.NoVM.bin GalleryRemote.1.5.Linux.NoVM.bin.bk
```

```
cat GalleryRemote.1.5.Linux.NoVM.bin.bk | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > GalleryRemote.1.5.Linux.NoVM.bin
```

```

sh GalleryRemote.1.5.Linux.NoVM.bin
```

---

### Post by Chireru on 2006-11-14
> **remarks said:**
> ```
cp GalleryRemote.1.5.Linux.NoVM.bin GalleryRemote.1.5.Linux.NoVM.bin.bk...
Okay, I tried that with the NoVM version, and it gave me this error...  it looks like I'm missing a piece of the GTK Toolkit?  I hunted around in synaptic, and I dont' see anything AWT..
[code]./GalleryRemote.1.5.Linux.NoVM.bin
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.70)
   at java.awt.Window.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at com.zerog.ia.installer.LifeCycleManager.f(DashoA8113)
   at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
   at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
   at com.zerog.ia.installer.Main.main(DashoA8113)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at com.zerog.lax.LAX.launch(DashoA8113)
   at com.zerog.lax.LAX.main(DashoA8113)
Caused by: java.lang.NoClassDefFoundError: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...11 more
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)
```

So I tried the VM version, and that installed fine, but when I try to run it, it gives me the same thing :(
```
GalleryRemote$ ./Gallery_Remote
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/home/tyler/Programs/GalleryRemote/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
```

---

### Post by remarks on 2006-11-14
I had the same problem as you initially and it worked for me... have a look here:

[[COLOR="Red"]>>>link<<<[/COLOR]]("http://gallery.menalto.com/node/50926")

---

### Post by remarks on 2006-11-14
> **Chireru said:**
> Okay, I tried that with the NoVM version, and it gave me this error...  it looks like I'm missing a piece of the GTK Toolkit?  I hunted around in synaptic, and I dont' see anything AWT..
```
./GalleryRemote.1.5.Linux.NoVM.bin
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.70)
   at java.awt.Window.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at com.zerog.ia.installer.LifeCycleManager.f(DashoA8113)
   at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
   at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
   at com.zerog.ia.installer.Main.main(DashoA8113)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at com.zerog.lax.LAX.launch(DashoA8113)
   at com.zerog.lax.LAX.main(DashoA8113)
Caused by: java.lang.NoClassDefFoundError: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...11 more
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)
```

So I tried the VM version, and that installed fine, but when I try to run it, it gives me the same thing :(
```
GalleryRemote$ ./Gallery_Remote
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/home/tyler/Programs/GalleryRemote/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
```

Ok... I can get the same error as you if I change my default javm.

Have a look and see what your defualt is:

```
sudo update-alternatives --config java
```

Mine is set to "/usr/lib/jvm/java-1.5.0-sun/jre/bin/java"

If I change it to "/usr/bin/gij-wrapper-4.1" I get the same error as you.

You may need to install a different version of Java Virtual Machine.  The easiest way is to use Automatix or some such auto installer script.

Good luck...

---

### Post by Chireru on 2006-11-15
> **remarks said:**
> Ok... I can get the same error as you if I change my default javm.
My Default java provider was /usr/lib/jvm/java-gcj/jre/bin/java...  tried changing it to /usr/bin/gij-wrapper-4.1, and I get the same issues.

I installed Sun JRE 1.5.0-09, selected that, and it still does the same thing. :(

---

