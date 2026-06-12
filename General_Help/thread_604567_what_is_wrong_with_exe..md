---
title: "what is wrong with exe. ?"
date: 2007-11-06
forum: General Help
---

### Post by the lemming on 2007-11-06
Before I get shouted down by people who say that Linux is nothing like Microsoft I have to ask why doesn't Linux have something as simple as the concept of an exe. file?

something like an exe file would make life a whole lot more simple for people like me with very limited knowledge of what goes on under the bonnet of a computer's engine.

---

### Post by LowSky on 2007-11-06
Two thing come to mind

.deb
.rpm

both seem to be the closest thing we have to excutable file structures

---

### Post by Shin_Gouki2501 on 2007-11-06
i think there is sothing similar:
try read these:
[http://en.wikipedia.org/wiki/Executable_and_Linkable_Format](http://en.wikipedia.org/wiki/Executable_and_Linkable_Format)

---

### Post by eye208 on 2007-11-06
Are you talking about .exe files in general or setup.exe files in particular?

---

### Post by finer recliner on 2007-11-06
> **LowSky said:**
> Two thing come to mind

.deb
.rpm

both seem to be the closest thing we have to excutable file structures

.exe is much more than just an application installer (which is what you seem to be comparing it to).

in linux, file formats are not a necessary part of the file name (in general). instead the format of the file is usually stored as "magic numbers" inside the file (yes that is what they are really called, look it up in wikipedia). there are many more types of files that run natively in linux than window's sole exe. you have shell scripts, interpreted code (i.e. python, perl) and binary data (what you consider exe), and probably more. 

:popcorn:

---

### Post by eldragon on 2007-11-06
what do you need .exe for?
its the sole reason social engeneering virus infections exist.

having a executable flag on the filesystem is much better..

---

### Post by timcredible on 2007-11-06
is what you're really saying is that you would like to try linux but don't want to learn anything new?  c'mon man, linux is **different** than windows, **not more difficult**.

---

### Post by az on 2007-11-06
> **the lemming said:**
> Before I get shouted down by people who say that Linux is nothing like Microsoft I have to ask why doesn't Linux have something as simple as the concept of an exe. file?

something like an exe file would make life a whole lot more simple for people like me with very limited knowledge of what goes on under the bonnet of a computer's engine.

I assume you mean the ability to surf the web, find some program that you are interested in running and click on it to install?

That's called binary-compatibility.

No.  GNU/linux is not binary-compatible.  It is source-compatible which is why the OS works so well.  Binary-compatibility slows down development.  By making the interface at the source level easiest, it's easier for people who want to contribute to the code.

Not to mention the security aspects of binary-compatibility are terrifying.  An analogy would be to compare how we now raise our kids.

In the "good-old-days" there were no child-molesters (there were, of course, but no one wanted to talk about it).  Children were free to talk to strangers.  We now know that this is dangerous and as sad as it may be, my children know that they should not talk to strangers if Mommy or Daddy are not there.

Unsuspecting computer users should not click on binary-only applications that they find on the internet without their Mommy or Daddy's approval (I mean, proper authentication).  Using software repositories provided by your distro allows you to install only authenticated applications in binary form.

---

### Post by jrharvey on 2007-11-06
> **az said:**
> I assume you mean the ability to surf the web, find some program that you are interested in running and click on it to install?

That's called binary-compatibility.

No.  GNU/linux is not binary-compatible.  It is source-compatible which is why the OS works so well.  Binary-compatibility slows down development.  By making the interface at the source level easiest, it's easier for people who want to contribute to the code.

Not to mention the security aspects of binary-compatibility are terrifying.  An analogy would be to compare how we now raise our kids.

In the "good-old-days" there were no child-molesters (there were, of course, but no one wanted to talk about it).  Children were free to talk to strangers.  We now know that this is dangerous and as sad as it may be, my children know that they should not talk to strangers if Mommy or Daddy are not there.

Unsuspecting computer users should not click on binary-only applications that they find on the internet without their Mommy or Daddy's approval (I mean, proper authentication).  Using software repositories provided by your distro allows you to install only authenticated applications in binary form.


Basically he is trying to say this. In windows if you want a cool new instant messenger then you go find it, download and install. Allong with this snazzy new messenger comes a weatherbar, searchbar, registry cleaner, spyware, and a whole bunch of other CRAP that you dont want on your computer. Linux has the all time easiest way to install programs EVER! If windows had a synaptic package manager MAYBE I would use it more. 
Acually I would still use linux but at least windows would be a bit safer.

---

### Post by aitorcalero on 2007-11-06
> **the lemming said:**
> Before I get shouted down by people who say that Linux is nothing like Microsoft I have to ask why doesn't Linux have something as simple as the concept of an exe. file?.

Why not the opposite? Why the need for an exe file or even extensions?

---

### Post by leksdraven on 2007-11-06
> **the lemming said:**
> Before I get shouted down by people who say that Linux is nothing like Microsoft I have to ask why doesn't Linux have something as simple as the concept of an exe. file?

something like an exe file would make life a whole lot more simple for people like me with very limited knowledge of what goes on under the bonnet of a computer's engine.
[COLOR=Gray] First, I'm sorry you feel that you will be shouted down by Linux users for speaking of Microsoft. Not all of us hate Microsoft (even if we all did it still would not be right to attack someone else because they do not), and I for one enjoy using Windows.

(BTW, I think it is ridiculous that I have to apologize for the Linux community's behavior. Some don't even realize that they are part of the problem.)[/COLOR] 

[COLOR=Black] Second, Linux does have "something like an exe file." It's called a bin (short for binary) file. Just like exe files, bin files should run after you double-click on them (all files in Linux have an executable bit. If this bit is off then it will not run).

However, if you are specifically speaking of a setup exe (which actually has a .msi extension [OS X's has .pkg]) then that's something different. By default, Ubuntu (a Linux distribution) does not come with a *software installation runtime* like Mac or Windows. Though, some projects exist which aim to bring this kind of functionality to Linux distributions.

We do have *packaged-for-installation* alternatives. The most common are called deb and RPM files. Debian and Ubuntu (among others) use deb files. Red Hat and Novell (also among others) use RPM files. There are some differences between each kind but not enough to be completely incompatible with each other (there are programs that can convert one into the other, and vice versa). These are simply installation files, though, not installation wizards. In Ubuntu, double-clicking one of these will open an installer application which will allow you to install the contents of the deb file (usually an application) and also any other required software.[/COLOR]

---

### Post by eye208 on 2007-11-07
> **az said:**
> GNU/linux is not binary-compatible.
It is binary-compatible at application level.

---

### Post by insane_alien on 2007-11-07
linux has this. just none of them have .exe in the name(microsoft has probably patented it or something anyway) they are called binarys(or blobs or .run or executables or ... well, theres a lot) 

for nstance, on this laptop, i have a file called 'fsg-4.4' no extension, but the executable bit is enabled. if i double click on this(like on a .exe in windows) i get version 4.4 of owen piettes falling sand game showing up. just like if i double clicked the .exe in the windows version.

now, seeing as there tend to be huge differnces between systems(different kernels, different modules different OS's in the open source world and binaries are horrible at handling this, the best way to distribute something is as the source code. this means that no matter who downloads it, assuming they have a suitable compiler, will be able to run it.

sure, its a tad more complex but there is always someone out there who will make a compiled version for you if you ask nicely(that is assuming it isn't in the repos and you can get a binary there.

---

### Post by Rinzwind on 2007-11-07
> **the lemming said:**
> Before I get shouted down by people who say that Linux is nothing like Microsoft I have to ask why doesn't Linux have something as simple as the concept of an exe. file?

something like an exe file would make life a whole lot more simple for people like me with very limited knowledge of what goes on under the bonnet of a computer's engine.

The whole problem with this is that Microsoft decided to actually have extension that have a function.

Look at it like this:

cp TEST.EXE TEST

Under Windows: you can't start TEST but it IS an executable.
Under Linux both files behave the same. 

So copying a file to a new name under Windows changes the function of the file!
Don't you think that's weird too?

---

### Post by az on 2007-11-07
> **eye208 said:**
> It is binary-compatible at application level.

No.  An application compiled on one version of a distro may or may not work on another version of that distro.  Not to mention another distribution altogether.   There is no stable binary interface.

---

### Post by weblordpepe on 2007-11-07
The short answer is that Windows has not evolved to the point of Debian/Ubuntu.

Ubuntu's way is the superior way - it allows software to be trusted on a huge scale, and also managed automatically.

Windows has the Windows Installer (.MSI) files. They are files with scripts in them, in which Windows installs the files, not the application.

The easiest way to think of it is that Ubuntu & it's repositories is like having every software title in the world on Windows Update.

---

