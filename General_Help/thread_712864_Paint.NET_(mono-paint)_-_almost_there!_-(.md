---
title: "Paint.NET (mono-paint) - almost there! :-("
date: 2008-03-02
forum: General Help
---

### Post by Znupi on 2008-03-02
Well, since Paint.NET is the only drawing program that works for me (I have a habit of sticking to the first thing I learned and not being able to switch to something else.. and Paint.NET is the first drawing program I learned how to use), I thought I'd give it a try on my Ubuntu (since my Windows partition is all messed up, full of viruses etc.). So I googled and found this: [http://tirania.org/blog/archive/2007/Dec-21.html](http://tirania.org/blog/archive/2007/Dec-21.html) . First thing that came to mind: "AWESOME!". I did some fiddling around, installed some packages, downloaded the source through SVN and tried to install it:
```

$ ./configure
Looking for required packages

paintdotnet has been configured with 
        prefix = /usr/local
        config = RELEASE_AND_PACKAGE_ANY_CPU

```
```

$ sudo make
... lots of things...
error CS0006: cannot find metadata file `System.Runtime.Serialization.Formatters.Soap'
Compilation failed: 1 error(s), 0 warnings
make[1]: *** [bin/Release/PaintDotNet.Data.dll] Error 1
make[1]: Leaving directory `/home/felix/src/paint-mono/Data'
make: *** [all-recursive] Error 1

```
:( I feel like I'm so close! Why that error? What should I do? Anyone else came across this?

---

### Post by Znupi on 2008-03-02
Bump :(
I realized I had mono 1.2.4 although on that site it said I should have mono 1.2.6 so I downloaded that from the mono website and installed it.
```

o$ mono -V
Mono JIT compiler version 1.2.6 (tarball)
Copyright (C) 2002-2007 Novell, Inc and Contributors. www.mono-project.com
        TLS:           __thread
        GC:            Included Boehm (with typed GC)
        SIGSEGV:       normal
        Notifications: epoll
        Architecture:  x86
        Disabled:      none

```
But it seems my mono-gmcs package is still at version 1.2.4 (I can see through Synaptic). How can I upgrade that, too?

---

### Post by Znupi on 2008-03-02
I've done it! I copied the file in /home/felix/mono-1.2.6/bin/gmcs to /usr/bin and it worked. Unfortunately, the buttons under the window menu (under the toolbar with File, Edit, etc) don't show up :(

---

### Post by brienc on 2008-04-14
Thanks for the tip, that helped me get it working!

---

### Post by dsiembab on 2008-04-18
I totally agree I think paint.net is one of the best programs out their for visual graphics. I actually thought the project was dead.

---

### Post by stinger30au on 2008-04-18
> **dsiembab said:**
> I totally agree I think paint.net is one of the best programs out their for visual graphics. I actually thought the project was dead.



nope. alive and strong

[http://www.getpaint.net/](http://www.getpaint.net/)

---

### Post by ibuclaw on 2008-04-18
I'm on Hardy, so I didn't get that problem. (since 1.2.6 is already installed from the repository!)

I love google code so much!
First Adobe Photoshop CS2 in WINE, and now this!
:KS:popcorn::KS

Translation for the blue text.

The buttons dont work!
Sorry for my language, but typing letters opens the menu bar.

Basically, type in "F" and the File menu opens, making it impossible to type in a complete sentence.
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=66373&stc=1&d=1208555507[/IMG]](http://ubuntuforums.org/attachment.php?attachmentid=66372&stc=1&d=1208555328)

---

### Post by denar on 2008-07-01
if u have some error in make
install **MonoDevelop** and open **paintdotnet.sln** and click F5 to run
if you see in **apllcationoutput** 
**Assembly '/home/ebrahim/paint-mono (another copy)/Resources/bin/Debug/PaintDotNet.Resources.dll' doesn't have an entry point.**
dabble click in **solution paintdonet** >> **Startup Properties**
in Single **Startup Project** chose **paintdonet** and click ok
now retry click F5 to run
and now if show to u message or in **apllcationoutput** show this
[B]-----HERE------
Got System.Drawing.Rectangle[] get_ClipRectangles() and System.Windows.Forms.Hwnd ObjectFromHandle(IntPtr)
-------Finished--------[/B]
thats mean ok now retry $./configure $make #make install
if install fine just to run type "paintdotnet" on the shell

i test this method in hardy and okk

---

