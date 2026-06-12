---
title: "How do i install packages that are not in the repos?"
date: 2007-04-15
forum: General Help
---

### Post by mshale on 2007-04-15
ok, I noticed that the repositories have not caught up with the newest versions of the software.  I have a new version of k9copy I'd like to install, but i don't know exactly how to go about installing that on my machine.  Any suggestions would be greatly appreciated!  :D

---

### Post by Maestro23 on 2007-04-15
Is it a .tar, .deb., .rpm, .bin, .sh?  Any of the following links will help:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

*Make sure and read the documentation that comes with the program as well.

---

### Post by mshale on 2007-04-15
Here is the file name>  k9copy-1.1.1-3.tar.gz

do you know what to do that extension?

---

### Post by Maestro23 on 2007-04-15
> **mshale said:**
> Here is the file name>  k9copy-1.1.1-3.tar.gz

do you know what to do that extension?

You will be compiling from souce with that.  Can get very messy because you are going to run into dependency issues.  Read the section on[COLOR="Red"] installing from source[/COLOR] on any of those links I gave you.

Section 4 here: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

*Make sure you read the INSTALL/README doc in the extracted directory once you run the tar command on the file.

---

### Post by mshale on 2007-04-15
hmm... that seems difficult.  can i use alien and make it a .deb file?  if not, oh well, i guess i'll just build it myself... :(

*update* ok, here i am building this myself.  i have the build essential package thing.  i type tar ```
-xvzf k9copy-1.1.1-3.tar.gz
``` and i get this error: 

```
matt@matts-laptop:~$ tar -xvzf k9copy-1.1.1-3.tar.gz
tar: k9copy-1.1.1-3.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous error

```

What do I do with that crap?? lol  and yes, the file is located on my desktop...

---

### Post by cstudent on 2007-04-15
The version in the Feisty repos looks like it is just the previous release version to the one you downloaded. What changes were made? Are they changes that would make much difference to you right now? To build from source you will need to have the correct build environment installed, like c++ for example. I didn't research what language the program was written in. You also have to make sure you have all the build dependencies met, like what other packages need to be installed first and what version level do they need to be at. Building a .deb file won't make any difference. You have to meet the same criteria. A deb is just a program built from source and packaged into a archived file that can be installed later. You still go through pretty much the same steps.

Unless there is some reason you need the newer version, I wouldn't worry with it. But then it can also be a real learning experience too.

---

### Post by Maestro23 on 2007-04-15
Very good advise posted by cstudent.  I don't believe that there are glaring differences between the version in the repositories and the latest version on the site.  Check the release notes.

To the OP, you are new to Ubuntu/Linux. Trying to compile something from source right now  is only going to lead to frustration.  I would hold off compiling anything from source until you know your way around Ubuntu a little better.  What you want right now, is a system that works and you can do the things you want on it.  Just my 2 cents.

Below are some links that will help you understand how Ubuntu does things.

Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

Community Docs: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Using the Terminal: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Top 10 Commands for noobs: [http://blog.lxpages.com/2007/02/25/top-10-linux-commands-for-newbies/](http://blog.lxpages.com/2007/02/25/top-10-linux-commands-for-newbies/)

Graphic Card Drivers
ATI supported cards: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Installing Nvidia Drivers:[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

How to Change Default OS: [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29)

Getting rid of junk: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by mshale on 2007-04-15
yes, the learning experience would be nice... 

the reason i wanted to update the k9copy is that the one i have keeps crashing on newer dvds.  it seems like they all have structure protection, and i thought that maybe the new version had a fix for that... maybe, or maybe not... who knows!!  but i would like to learn how to build it all myself... i edited my previous post

---

### Post by mshale on 2007-04-15
cool, i've gotten myself past the errors.  now i'm simply walking through dependency hell... any suggestions for this?  any thoughts on why i don't already have all of the dependencies since i had a previous version that worked?? lol oh well, it's all fun and games until i break my system :D

---

### Post by mshale on 2007-04-15
so, k9copy is for kde, and i'm running gnome.  so therefore i run into errors when in try to build it from source...  there is a readme in the package i downloaded: install from sources:

```
make -f Makefile.cvs
./configure --prefix=/usr
make
make install      (as root)


k9copy can now copy dvd with bad sectors.
for a faster copy from a dvd with bad sectors : reduce the readahead for the drive :

as root: hdparm -a8 /dev/dvd
```

any suggestions as how to handle this?  i'm learning here... lol

here is some of the code that i am putting in the terminal to try to compile this:

```
matt@matts-laptop:~/Desktop/k9copy-1.1.1-3$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU

...

checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
```

---

### Post by zenwalker on 2007-04-15
> checking for KDE... configure: error:

You got not KDE or any of its related libs package installed. Hence errors.

---

### Post by mshale on 2007-04-15
ok, that makes sense.  how do i get kde headers or he files i need to get this project on the road?? I guess my question is "how do i get the kde headers i need when i'm running gnome?

---

### Post by mshale on 2007-04-15
I got past the ./configure and now the make failed.  I get these errors:
```

collect2: ld returned 1 exit status
make[3]: *** [k9copy] Error 1
make[3]: Leaving directory `/home/matt/Desktop/k9copy-1.1.1-3/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/matt/Desktop/k9copy-1.1.1-3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/matt/Desktop/k9copy-1.1.1-3'
make: *** [all] Error 2

```

any help?

---

