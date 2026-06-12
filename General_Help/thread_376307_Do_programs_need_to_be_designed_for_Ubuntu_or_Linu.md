---
title: "Do programs need to be designed for Ubuntu or Linux?"
date: 2007-03-04
forum: General Help
---

### Post by Malware on 2007-03-04
Sorry if this isn't the best place for this post. Ive never tried linux or ubuntu and I am curious as to how many of my programs will work if i were to transfer over.

I have read a couple guides on using Ubuntu and they offer links to compatible software alternatives to stuff like Adobe Photoshop or a cd creater etc.

Does this mean that Adobe Photoshop will not work in Ubuntu?

I am not sure i will be able to use Ubuntu if products from adobe do not work or Maya and 3ds max. Do new games work either?

Thx for any info, I know this post might sound dumb to advanced users but like i said i never used Linux before.

---

### Post by timjayko on 2007-03-04
you can use wine a windows emulator in ubuntu to run .exe programs and there is a gaming program called cedega that allows you to install games you download or from the disc.. you can check out which games run well under cedega at transgaming.org.. usually you want to try only games with 4 or 5 stars.. I heard that you can get world of warcraft running pretty nice with wine if thats the game you play

---

### Post by NickPresta on 2007-03-04
For software in your repository (when you view available applications through Synaptic), those applications are specific designed for Ubuntu (or made compatible with Ubuntu).
Ubuntu uses DPKG/APT package manager so you will want to look for software packages that end in DEB (.deb) but be warned, this does not mean they will work on Ubuntu! Debian and any other distribution that uses DPKG/APT can use DEB packages so you will want to check with the author (via documentation or email) to see if the package will work on Ubuntu or if there is a Ubuntu specific package.

For software you want to compile on your own (which you shouldn't need to do unless you require the latest or development version), you will need to check the dependencies and install them via your package manager (Synaptic). You may need to compile some of your dependencies too, depending on the package.

Ideally, you will want to use the Linux equivalent instead of trying to use Windows software on Ubuntu.
Read this: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
Then look at this list: [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

Remember, Linux is not Windows so forget your Windows habits and enjoy using Ubuntu - it really is a pleasure.

---

### Post by Malware on 2007-03-04
thank you for the replies, I seem to be in more over my head than i thought before posting but your links and info is very informative.

---

### Post by lotu on 2007-03-04
The short answer is yes programs must be designed to run under Linux/Ubuntu and no things like 3ds Max and most games will not work under Linux
The long answer is what really matters is the computer you have running you applications and the operating system comes in second.  So many applications are very easy to transfer from windows to linux, on the other hand a lot aren't.  I looked around on goolge and it looks like Maya has a linux version of their software, so that should work under linux with no problems.  If you just need a program and aren't tied to Photoshop or 3ds Max you could try other programs that have similar functionality like the Gimp and Blender, that do work under linux.  These work differently form their counterparts so you may have to relearn how to do some stuff.  
Finally games almost no games are designed for linux so some exceptions are UT, Doom and Quake.  The rest of the games can sometimes be run with a program called WINE it pretty much acts as an interpreter between the windows program and linux, and when it works the games run as well or better than they do in windows.  However, that is only when it works and if you are new to linux it probably won't work for you unless you have somebody help you or are nice luck and someone has written a tutorial on how to make the game run.  Summarily other programs like photoshop can be used with WINE but only if you are lucky go look at [http://appdb.winehq.org/appbrowse.php?catId=0](http://appdb.winehq.org/appbrowse.php?catId=0) to see how well different programs work.

So if you want to try linux I suggest you get a live cdrom and boot your computer with that, you will still be able to run windows and it won't change your computer at all.   If you like that then try to dual boot you computer and so you can switch between windows and linux so you can both operating systems on one computer.

---

