---
title: "How to start programming in Linux"
date: 2008-02-22
forum: General Help
---

### Post by Ioky on 2008-02-22
After using Linux for a while, I am pretty happy with the system. So I am thinking to go back to programming, and do some fun thing with it. I did a lot of web development under Linux with bluefish. but when it comes to Java and C++. I have no idea where to start. long time ago, when I using windows and Dos, I was given a complier and a text editor goes along with it. In Linux I am a bit lost, and don't know where to start, and what package I should install. 

In general, I do text base programming along with 2D graphic programming, (never did GUI yet but thinking to start it from now). So where I can get started? And what good tools are recommended ?

Thanks.

---

### Post by kaens on 2008-02-22
> **Ioky said:**
> After using Linux for a while, I am pretty happy with the system. So I am thinking to go back to programming, and do some fun thing with it. I did a lot of web development under Linux with bluefish. but when it comes to Java and C++. I have no idea where to start. long time ago, when I using windows and Dos, I was given a complier and a text editor goes along with it. In Linux I am a bit lost, and don't know where to start, and what package I should install. 

In general, I do text base programming along with 2D graphic programming, (never did GUI yet but thinking to start it from now). So where I can get started? And what good tools are recommended ?

Thanks.

Well, first you'll need to install build-essential if you want to do any compiling.

There's a lot of editors - I prefer emacs. It has a learning curve, but learning it will practice your coding chops and after a bit you will be super efficient at whatever editing task you want to do. 

For graphics, especially 2d graphics, I'd reccommend SDL as it's cross-platform and has bindings for just about every language in existence, and good documentation.

For GUI systems, I'm not experienced enough to comment but I hear QT is pretty nice.

---

### Post by neoAnderson on 2008-02-22
There's a variety of editors available out there: vi(m) is a very powerful text editor. If you want something more along the lines of any IDE in Windblows, Kate is really nice - it has features such that you can open multiple files at the same time and switch easily between them, and also copy/paste, and you can minimize logical blocks of code to have a look from a higher level - just like Visual Studio.

If I were you I would give Kate a try. It comes with KDE, or you can install it alone.

The compiler for Java is called javac and the interpreter is java. The compiler for C++ is called g++. Install them using Synaptics and you will be good to go. 

There you are - that's the way to start.

---

### Post by lifewithryan on 2008-02-22
If your going to do Java make sure to install the Sun Java package from the Ubuntu repos instead of the "gij" compiler.  I've noticed that the "gij" compiler doesn't always work with all java apps, etc.

Also, if you are using Ubuntu/Compiz...and are noticing that your swing apps are showing up with nothing in the GUI but blank windows, try this:

```

export AWT_TOOLKIT=MToolKit

```

took me forever to figure that out.

---

### Post by Ioky on 2008-02-22
Thanks so much for the help

---

