---
title: "2 questions"
date: 2008-03-12
forum: General Help
---

### Post by oniell on 2008-03-12
First a statement.
I'm really new to Linux. Never done it before so bear with me.

Ok, now, Number one.
 How do I remove gutsy? I tried using XP to remove the partition. Bad idea. It would not allow the boot selector thing to load. I reinstalled it and would like to remove it the correct way..


Number 2
Can I install a version  I have from a LIVE CD? I got it from a programming book and it comes completely loaded with xampp and my other web dev stuff. The thing is that it does not have an install icon like most of the others.

I'm sorry if these have been answered, but I could find nothing.

---

### Post by Afkpuz on 2008-03-12
Well, if you want to replace gutsy, format your gutsy partition with Gparted and then install your new OS on that partition.  If you want detailed instructions on using gparted, I can help you out there too.

---

### Post by kuja on 2008-03-12
I've never tried to do it, but i assume the correct way would be to boot into windows, pull up a cmd.exe window , then run fixmbr, then reboot to test that it isn't using grub anymore. Then you'll be free to remove anything you want. 

If it doesn't have an install option it might not be easy to do - nevertheless the files are there so it can probably be done, with a bit of work.

---

### Post by oniell on 2008-03-12
actually the fixmbr is only used through the recovery console. I'm gonna do that.

Does anyone know how I could install from that CD?

---

### Post by jespdj on 2008-03-12
The normal way to install Ubuntu is to download a Live CD from [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu) and select "Install" in the boot menu of the CD, or double-click the Install icon on the live desktop.

You are using a CD from a programming book that sounds like it isn't the standard Ubuntu CD. You didn't tell us which book it is, so it's kinda hard to help you with this.

You could just install the standard version of Ubuntu and [get XAMPP here](http://www.apachefriends.org/en/xampp-linux.html) and install it. Note: I have no experience with XAMPP but I remember reading that it is available as a 32-bit package only; that means it will be easier to install on 32-bit Ubuntu (i.e. do not download and install 64-bit Ubuntu).

---

### Post by kuja on 2008-03-12
If you wanted to do it in 64-bit ubuntu, it would probably be as easy as :dpkg --force-architecture --install" ing the package, then running a script called getlibs to handle any 32-bit lib depends. Not too bad, (ie: not a show stopper)

---

### Post by oniell on 2008-03-12
Now, this dist. came with "Practical PHP and MySql" book. I have no idea if it's a 32 or 64 bit. If it's 32 can I run the same command?

That brings something else to mind. I know with windows you have to have 64bit hardward. Same with this? The stuff I have is 32bit I believe. 

On a side note, I thought about just installing xampp. The problem is that I could not get my wireless here on my dev machiene to work. The version I downloaded seemed to be missing the device manager and that(I forget the name) thing to use windows wireless drivers. As a result, the wireless was not working correctly. Is there I version of ubuntu that has that?(If you like I could get a screen shot of what my administration list looks like)

---

### Post by oniell on 2008-03-12
Sorry,



bump

---

### Post by kuja on 2008-03-12
> **oniell said:**
> Now, this dist. came with "Practical PHP and MySql" book. I have no idea if it's a 32 or 64 bit. If it's 32 can I run the same command?

That brings something else to mind. I know with windows you have to have 64bit hardward. Same with this? The stuff I have is 32bit I believe. 

On a side note, I thought about just installing xampp. The problem is that I could not get my wireless here on my dev machiene to work. The version I downloaded seemed to be missing the device manager and that(I forget the name) thing to use windows wireless drivers. As a result, the wireless was not working correctly. Is there I version of ubuntu that has that?(If you like I could get a screen shot of what my administration list looks like)

Commands by far and wide are the same with small exceptions (mostly flags for setup and compiling).

Yeah, you'd have to have 64-bit hardware to run 64-bit Linux. (keep in mind, the Core 2 Duo CPUs are also 64-bit)

Wireless wasn't working? That sounds like a real pain .... but that's probably a topic worthy of another thread.

---

### Post by oniell on 2008-03-12
ok, so I run that command in the console? dpkg --force-architecture --install

If not, where do I run it?

I have mostly 32bit hardware. The only part that might be 64 is my AMD 2x core CPU.

Ya, the device manager was not there neither was the snyaptic package manager part that would allow the install of windows drivers. I could not even view the wireless card much less install a driver. That's another topic though...

---

### Post by kuja on 2008-03-12
That command has to be run on a .deb package, otherwise it'll just print the usage info or throw an error, but yeah, just run it in a shell.

I'm pretty sure that AMD processor would be 64-bit, as they didn't even make a dual core CPU until the Athlon 64 X2's.

---

### Post by oniell on 2008-03-12
> **kuja said:**
> That command has to be run on a .deb package, otherwise it'll just print the usage info or throw an error, but yeah, just run it in a shell.



Forgive me, but what?


I'm pretty sure the CPU is 64bit(short of going and booting the computer....thats about the only part though....little good...


Just a side note. I ran fixmbr and it worked spiffy. now I have to find a good, working dist of this.

---

### Post by kuja on 2008-03-12
> **oniell said:**
> Forgive me, but what?


I'm pretty sure the CPU is 64bit(short of going and booting the computer....thats about the only part though....little good...


Just a side note. I ran fixmbr and it worked spiffy. now I have to find a good, working dist of this.

When one refers to a 64-bit computer they're referring only to the CPU, you don't need any other "special" parts or such.

That was a command to install a deb package (in particular, it was to force the installtion of a i386 package on a x86_64 setup). deb packages are ... well, [wikipedia explains it well enough](http://en.wikipedia.org/wiki/Deb_(file_format))

---

### Post by oniell on 2008-03-12
Hmm..ok, I can't say I knew that.


I know what a deb is now...now how do I run that command?

---

### Post by oniell on 2008-03-12
Sorry, I'm just new at this. Windows, no. But linux yes.

---

### Post by kuja on 2008-03-12
> **oniell said:**
> Hmm..ok, I can't say I knew that.


I know what a deb is now...now how do I run that command?

First things first, pull up a shell and type "uname -m"

If you've installed the 32-bit Ubuntu (likely) It'll read i686 or i386, in which case you wouldn't need to bother. I was just noting the above in the case you need to reinstall and you used the 64-bit ubuntu (seeing as your hardware should be capable), what you would need to do. If it says x86_64 - then all you need to do is attach the file name to the end of that command and run it, then search ubuntu forums for getlibs, install getlibs, and run it against the xampp binary to take care of dependencies (ie: *getlibs $(which xampp)*)

---

### Post by oniell on 2008-03-13
Ok, thanks for your help. The issues are resolved. I got xampp installed.

---

