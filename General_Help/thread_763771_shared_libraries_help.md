---
title: "shared libraries help"
date: 2008-04-23
forum: General Help
---

### Post by lookforlohith on 2008-04-23
hi brothers please clear my doubts

1. i wrote a program wen i was using fedora ... now im using ubuntu ,....

if i try to execute it its showing like this

./lohishell: error while loading shared libraries: libtinfo.so.5: cannot open shared object file: No such file or directory


-> so does executable files need header files

-> wat is mean by shared libraries

-> wat is shared object file

please help me learning these

2. my wine is not working .... im unable to use turbo-c of windows in ubuntu(not able to use any windows software)

3. how to make graphics.h library  work in ubuntu

please help me teach me . thanks in advance

---

### Post by kidders on 2008-04-24
Hi there,

> **lookforlohith said:**
> -> so does executable files need header filesNo, but you do tend to need them to *build* things.

> **lookforlohith said:**
> wat is mean by shared librariesA shared library is a resource that exposes common functionality to your applications (eg how to draw text in a terminal, how to negotiate a network connection over SSL, how to talk to a bluetooth device, and so on). Using them saves you having to constantly re-invent the wheel.

Essentially, you won't be able to run the application you wrote on any computer that doesn't meet its dependencies, regardless whether it's running Fedora or Ubuntu. Afaik, libtinfo.so.5 is an ncurses library.

I'm not sure if I can help with your other questions ... A broken wine could be due to any number of things, and graphics.h is just a header file ... it doesn't really *do* anything. It's just a flat text file that describes the interface to a library.

---

### Post by pelviciabc1 on 2011-01-13
> **lookforlohith said:**
> hi brothers please clear my doubts1. i wrote a program wen i was using fedora ... now im using ubuntu ,....if i try to execute it its showing like this./lohishell: error while loading shared libraries: libtinfo.so.5: cannot open shared object file: No such file or directory-> so does executable files need header files-> wat is mean by shared libraries-> wat is shared object fileplease help me learning these2. my wine is not working .... im unable to use turbo-c of [[COLOR=#000000]windows[/COLOR]](http://www.rersoft.com/asf-video-file/convert-asf-to-avi.html) in ubuntu(not able to use any windows software)3. how to make graphics.h library work in ubuntuplease help me teach me . thanks in advanceThanks very much! Anyone have got the solution? I've been always concerned about it.

---

