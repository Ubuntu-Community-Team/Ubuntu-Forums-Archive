---
title: "RAD Development tools for ubuntu"
date: 2008-04-27
forum: General Help
---

### Post by GCoffee on 2008-04-27
Hello,

I'm looking for a RAD (Rapid Application Development) tool for ubuntu.

I checked out gambas and at one point had gambas 1 installed, but with gambas 2 I'm just having a load of problems... and I couldn't find gambas1/ Gambas in the repositories .... just gambas2.

I'm quite happy to use python as I heard that that is the best language for GTK+/GUI programming, which is what I am intending to do. 

I took a look at python and was just wondering how you compile the files into Linux and/or windows executables. I'm definitely going to need linux executables and if possible windows.

Sorry if this is in the wrong forum, I'm guessing its general but...

Thanks.

---

### Post by cmay on 2008-04-27
hi
those i know of 
there is boa contruktor for python that uses wxvidgets
there is lazarus that looks like delhi alot that uses freepascal compiler.
there is some other gui creation tools like glade and wxglade.

i like the idea of  lazarus best as i learned pascal two years ago and i dont know any python. i am learning c right now but to be honest the glade tools i find tricky 
i am not a programmer i just like the learning of the computer language as hobby so i dont know how great the tools i suggest are for your needs.
there is a programmering talk forum also here in ubuntu forums.
hope it helps.

---

### Post by fifth on 2008-04-27
The most complete rad ide environment on Linux is probably [Netbeans]("http://www.netbeans.org/") for Java development. All my main development is done in Java, and mostly using Netbeans.

I'm also trying out Python with the Qt framework ([PyQt]("http://www.riverbankcomputing.com")). For Qt ui design, you've got the [QT Designer]("http://trolltech.com/products/qt/features/designer"). You can pretty much use any editor you like, but I think [Eric]("http://die-offenbachs.de/eric/index.html") integrates with the designer.

I haven't played much with the Designer, since coding gui's is very straight forward with PyQt.

All of the above can be installed from the repos.

[Edit]
Just noticed that its GTK+ you're looking to do so my post probably didn't help much lol.
[/Edit]

---

### Post by GCoffee on 2008-04-27
> **fifth said:**
> 
Just noticed that its GTK+ you're looking to do so my post probably didn't help much lol.


Sorry, my mistake to! GTK+ is preferable as it is one of those multi-platform/independent thingamajig's (I like technical language...;))

I'm looking at pyqt now..

Cheers.

---

### Post by GCoffee on 2008-04-27
I checked out the repos and couldn't find pyqt... I'm looking at the QT 4 designer which seems pretty simple to use.

Does anyone know any good tutorials for it?

Thanks

---

### Post by fifth on 2008-04-27
> **GCoffee said:**
> I checked out the repos and couldn't find pyqt... 

From the command line; sudo apt-get install pyqt4-dev-tools

> 
I'm looking at the QT 4 designer which seems pretty simple to use.

Does anyone know any good tutorials for it?

Thanks

[Qt Designer Tutorial and User's Manual]("http://doc.trolltech.com/2.3/part1index.html")

---

### Post by kalaharix on 2008-04-28
I have to say that I have had nothing but joy from Gambas2. Install from Synaptic rather than Ubuntu package manager. Click on Gambas2 and it will check everything except one line which should be manually checked. Add the following to system, admin, software source, third party software:
deb [http://azores.linex.org/gambas-other/](http://azores.linex.org/gambas-other/) hardy main
(substitute gutsy for hardy if still on Ubuntu 7.1)

In time, this will upgrade from 2.0 to 2.5.

The documentation is not great, many of the examples have problems, most of the GambasForge examples have problems but the core product is great particularly if you come from a VB background.

It is only Linux. If you need cross-platform then PureBasic and REALbasic are two commercial options.

---

### Post by ivze on 2008-04-28
You may see code::blocks [http://www.codeblocks.org/](http://www.codeblocks.org/) with wxSmith plugin.
Very nice, provides basic functionality for RADing in C++ using wxWidgets cross-platform library. It is declared, that carefully-written programms will compile on both Windows and Linux.

---

### Post by GCoffee on 2008-04-28
I'm downlading pyqt now, might seem a simple question but do you use idle or something else?

---

### Post by fifth on 2008-04-28
> **GCoffee said:**
> I'm downlading pyqt now, might seem a simple question but do you use idle or something else?

Its really your own personal preference. I've tried most of the editors, Eric is probably one of the most complete (although it just didn't suit me for some reason), or you can download the open source version of Komodo.

Personally i use Jedit since i'm not bothered about integrating with QT Designer. With Jedit, i generally just work with the file browser docked to the left. This suits me as I'm not really into the 'Project' way of doing things - which most full ide's seem to try and force on you.

I don't use idle, but sometimes just have a console open running python for importing and/or testing my code.

Really any editor will do, most will support syntax highlighting for Python, eg Kate/Gedit etc.

---

### Post by fifth on 2008-04-28
Just another thought, you might want to check out some of the PyQt tutorials to get you started.

[Random google search tutorial]("http://www.zetcode.com/tutorials/pyqt4/")

---

