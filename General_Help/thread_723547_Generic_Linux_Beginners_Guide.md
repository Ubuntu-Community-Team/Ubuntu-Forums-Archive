---
title: "Generic Linux Beginners Guide"
date: 2008-03-13
forum: General Help
---

### Post by brnetonboy on 2008-03-13
I just installed Ubuntu 7.10 Gutsy Gibbon.

I have been searching all over the internet for several hours now. Including this forum, the Ubuntu website, other forums, even yahoo answers... I have not been able to find what I need... 

I am good with computers and pick things up pretty fast--I've installed and configured my own apache server with PHP before... but I am new to Linux and there are very simple things holding me up... I am hoping that someone can point me to a good beginners guide.

I don't need info on using the terminal--I already found a list of commands and I'm comfortable using it.

What I do need help with is the really really obvious things that nobody ever thinks to put in the instructions. Some example questions:

-When I install a program with Synaptic Package Manager, where does it go? There is no "Program Files" folder... 
-When I install a program with ./configure make make install, where does it go? The directory the terminal is in, or does it automatically go to the place it's "supposed" to go to?

-Once I install a program, how do I open it? In Windows, if all else fails, if no shortcuts were made, I could always go to "Program Files" and find the folder with the name of the program I installed, open that, and find the most important looking file with .exe at the end. Is there something like that I can do in Linux?

-Where are the filename extensions? What is the extension that demarcates the main executable file... aka is there something that corresponds to the windows .exe?

-I have a shortcut on my desktop and it points somewhere. In windows, you can right click, go to properties, and it shows the path of the thing it's pointing to. How do I do this in Linux?



So you see I'm ok with some of the more technical stuff, but nobody ever explained the most obvious things to me! Is there any sort of general guide out there on the internet that can help me? Mostly I need to know how to install new programs. I'm used to Windows.

Thanks so much.

---

### Post by ElijahLynn on 2008-03-13
I am new too. This might help you [http://ubuntuclips.org/](http://ubuntuclips.org/)

---

### Post by the-edmeister on 2008-03-13
Check out this one:
[http://lowfatlinux.com/](http://lowfatlinux.com/)

I am a noob, too.

---

### Post by PeterJS on 2008-03-13
> **brnetonboy said:**
> I just installed Ubuntu 7.10 Gutsy Gibbon.

I have been searching all over the internet for several hours now. Including this forum, the Ubuntu website, other forums, even yahoo answers... I have not been able to find what I need... 

I am good with computers and pick things up pretty fast--I've installed and configured my own apache server with PHP before... but I am new to Linux and there are very simple things holding me up... I am hoping that someone can point me to a good beginners guide.

I don't need info on using the terminal--I already found a list of commands and I'm comfortable using it.

What I do need help with is the really really obvious things that nobody ever thinks to put in the instructions. Some example questions:

-When I install a program with Synaptic Package Manager, where does it go? There is no "Program Files" folder... 

Probably in /usr/bin/, that's where most things end up, see the where are my files hiding link in my sig for a more complete over view.
> 
-When I install a program with ./configure make make install, where does it go? The directory the terminal is in, or does it automatically go to the place it's "supposed" to go to?

Make builds the program in place, and then make install copies it to it's final destination. I would suggest installing checkinstall and using it instead of make install, it will invoke make install in a wrapper and build the program in to a .deb package and install it for you, that way it can be uninstalled with synaptic.

> 
-Once I install a program, how do I open it? In Windows, if all else fails, if no shortcuts were made, I could always go to "Program Files" and find the folder with the name of the program I installed, open that, and find the most important looking file with .exe at the end. Is there something like that I can do in Linux?

In synaptic if you right click on a package one of the options is to show installed files, which will have two things that will help you here, a listing of all the files, it's probably the one in a bin folder with the same name as the package, and if that fails look for the .desktop menu entry, one of the elements in there is the name of the binary. If all else fails, locate is excellent finding thing.
```

locate *Thing I'm looking for*

```

> 
-Where are the filename extensions? What is the extension that demarcates the main executable file... aka is there something that corresponds to the windows .exe?

There isn't. Linux relies on magic and other finger print characteristics of files to identify them. To specifically identify if something is executable check it's file permissions. If it has execute permission, it's an executable.

> 
-I have a shortcut on my desktop and it points somewhere. In windows, you can right click, go to properties, and it shows the path of the thing it's pointing to. How do I do this in Linux?

If you right click on a desktop item, if it's a shortcut the far right tab should be volume (for disks), link (for locations), or launcher (for programs) and that will tell you where it points.

> 
So you see I'm ok with some of the more technical stuff, but nobody ever explained the most obvious things to me! Is there any sort of general guide out there on the internet that can help me? Mostly I need to know how to install new programs. I'm used to Windows.

Thanks so much.

Mostly synaptic :)
But for everything else:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

And a guide to everything else:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by koenn on 2008-03-13
> **brnetonboy said:**
> 
-When I install a program with Synaptic Package Manager, where does it go? There is no "Program Files" folder... 
-When I install a program with ./configure make make install, where does it go? The directory the terminal is in, or does it automatically go to the place it's "supposed" to go to?

/usr/bin, most likely, although some programs can end up elsewhere (eg /usr/sbin). This is a standard location that is part of the PATH, so if you just type the name of a program in a terminal, it will execute. you can also find the path to that program with 'which'
```
k@x:~$ which vmware-server-console
/usr/bin/vmware-server-console
```

Here's sort of Windows to Linux Quick Start. It's not really a beginner's guide, but more like an overview of what Windows power users / sysadmins would probably like to know to get a handle on Linux, like "how can i find a file if there are no drive letters" or "where is the Registry"
[http://users.telenet.be/mydotcom/howto/linux/migration02.htm](http://users.telenet.be/mydotcom/howto/linux/migration02.htm)

---

### Post by Feivel on 2008-03-13
Isn't this forum a Linux neophyte's dream?

---

### Post by brnetonboy on 2008-03-14
> **Feivel said:**
> Isn't this forum a Linux neophyte's dream?

Yes!! Thank you all! You have saved me hours of wading through millions of pages trying to find the relevant info I need! Those links are all very helpful, and your answers are great! If anyone else has good links, keep 'em coming!

---

