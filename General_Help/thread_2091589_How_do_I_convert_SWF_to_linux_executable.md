---
title: "How do I convert SWF to linux executable?"
date: 2012-12-05
forum: General Help
---

### Post by colobix on 2012-12-05
Hello. do any of you know how to convert adobe flash to linux executable, like they did here [http://redrogue.net/](http://redrogue.net/) ?

---

### Post by lildigiman on 2012-12-05
Can't say for sure, but it looks like the Flex Source code could have just been ported to some other compiled language in linux...?

So that being the case, they really aren't converting an swf to a linux executable.

Just a guess.

---

### Post by colobix on 2012-12-05
Ok so what have they done, and what software can this be done with?
I don't care if it's been converted or not.
I just wanna be able to do this with swf files.
The page I gave you was just an example. I don't to use that method

---

### Post by lildigiman on 2012-12-05
Like I said, someone probably took the time to port the source code (as in manually translate it to another language to be compiled to a linux executable). You can see it on their github for that example you shared.

Also, what do you mean you want to be able to do this with swf files? If I understand you correctly, then you can't do anything with a FooBar.swf file itself. You need the source code to be able to port it to another language. From there then compile that source file to an executable.

Tools to do this are a text editor and a lot of time, and preferably the knowledge base of a computer scientist/software engineer.

---

### Post by colobix on 2012-12-05
So there aren't any way to convert swf to linux executable ?

---

### Post by 3rdalbum on 2012-12-06
> **colobix said:**
> So there aren't any way to convert swf to linux executable ?

I thought the Flash authoring program could output to Linux, Mac and Windows binaries? But you would need the full Flash software and the source file (.Fla, not .swf).

---

### Post by dragonfly41 on 2012-12-06
I think you might be looking for a "wrapper" which imports an existing *.swf file (a game object?) as an asset and runs as a desktop executable?

I've done that before in Windows using Screenweaver but so far not in Linux.

Start by looking here ...

[http://www.swftools.org/](http://www.swftools.org/)

Also look at [http://haxe.org](http://haxe.org)

[http://stackoverflow.com/questions/69664/does-a-good-swf-to-exe-wraper-open-source-exists](http://stackoverflow.com/questions/69664/does-a-good-swf-to-exe-wraper-open-source-exists)


[COLOR=DarkRed][Later Edit]

The announcement by Adobe not to support future releases of flash in linux might make you rethink your strategy and perhaps consider HTML5?[/COLOR]

---

### Post by lildigiman on 2012-12-06
> **3rdalbum said:**
> I thought the Flash authoring program could output to Linux, Mac and Windows binaries? But you would need the full Flash software and the source file (.Fla, not .swf).

Hey, 3rdalbum, you might be right about being able to auto export to an executable; I've never developed any Flash before. Whether or not you can do this, you still need the source code to make a linux executable.

---

### Post by colobix on 2013-01-12
> **dragonfly41 said:**
> The announcement by Adobe not to support future releases of flash in linux might make you rethink your strategy and perhaps consider HTML5?[/COLOR]
But when I convert it to linux, it's not gonna be flash anymore. I mean, the format flash.
So are you saying I should first convert it to html5 and then to linux exe?

> **3rdalbum said:**
> I thought the Flash authoring program could output to Linux, Mac and Windows binaries? But you would need the full Flash software and the source file (.Fla, not .swf).
Probably. What program is that?
And is it available in the software center?
If not, where can I find it?

---

