---
title: "Rasterbator visualization problems with mono"
date: 2007-07-17
forum: General Help
---

### Post by TheNonBornKing on 2007-07-17
I'm trying to use the **[Rasterbator Standalone](http://arje.net/rasterbator)** to create large rasterized posters of images. It is released as an open source .NET application. It comes with a windows compatible binary and the source code.

I followed the directions **[here](http://screamz.madoka.be/wiki/index.php/Rasterbator_with_mono)** to compile the source including the use of a patch to use Linux directory style (/ instead of \) among other things. I had no problems compiling it but when I run it I get weird visualization problems with the buttons and objects. Text boxes are not in the right place or visible at all. Buttons are off screen somewhere. Resizing the window to try and find them does not help. I know that everything is there because I can tab over to it and use it, it's just not visible.

Here are some screen shots:
[[IMG]http://img357.imageshack.us/img357/5973/rasterprob1sf4.th.png[/IMG]](http://img357.imageshack.us/my.php?image=rasterprob1sf4.png)
[[IMG]http://img219.imageshack.us/img219/9660/rasterprob3wn8.th.png[/IMG]](http://img219.imageshack.us/my.php?image=rasterprob3wn8.png)

I am using Ubuntu Feisty Fawn and here is my mono -V:
Mono JIT compiler version 1.2.3.1, (C) 2002-2006 Novell, Inc and Contributors. [www.mono-project.com](www.mono-project.com)
        TLS:           __thread
        GC:            Included Boehm (with typed GC)
        SIGSEGV:       normal
        Architecture:  x86
        Disabled:      none

Here is the compiler output. The guide linked above says the 2 warnings are normal. 
mcs -out:../Rasterbator.exe -unsafe -resource:Rasterbator.MainForm.resources -r:System.Windows.Forms -r:System.Drawing -r:../itextsharp.dll *.cs
MainForm.cs(1685,8): warning CS0169: The private method `Rasterbator.MainForm.NumericUpDown4KeyUp(object, System.Windows.Forms.KeyEventArgs)' is never used
Rasterbator.cs(117,10): warning CS0169: The private property `Rasterbator.Rasterbator.Directory' is never used
Compilation succeeded - 2 warning(s)

I am also running on a Dell laptop if that is important. 

So is this problem with the source code or is there something I can do about it? I've seen screen shots from other people running it on Linux and they don't have this problem so I think it is my problem. :(

P.S. I'd like to use the Standalone version because it allows much finer resolution on the output than the web-based version, which is better with large source images.

---

