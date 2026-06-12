---
title: "[SOLVED] basics of building?"
date: 2007-10-17
forum: General Help
---

### Post by digitalhillbilly on 2007-10-17
Hi Listers! 

I found a while back a really great howto on building from sources basics, it included things like needed software, how to list build options, etc... I'm still a newb so like to reference these things as I go along. I did have it bookmarked but sadly I forgot to copy over my bookmarks before I zapped the drive and installed a nice fresh copy of Ubuntu Studio. ug. I've searched high and low on the forums for this page and cannot find it and was hoping it would ring a bell with someone here.

I think I can struggle through it ok but feel better with some reference.

Thanks!
dh

---

### Post by gsiliceo on 2007-10-17
Maybe it was this one?

How to install ANYTHING In ubuntu
[http://monkeyblog.org/ubuntu/installing.html#source](http://monkeyblog.org/ubuntu/installing.html#source)

---

### Post by digitalhillbilly on 2007-10-17
Thanks for the reply gsiliceo! No, this is not the one. The page I'm looking for I'm pretty sure was somewhere in the Ubuntu forums and was titled something like "howto: something something...". The author gives a great over view of building from sources. 

The two things I'm interested in from the doc are: software requirements, I can't remember if build-essential is all I need; and how to check available ./configure options. And some other bits of what I'm sure are immensely helpful info that have seem to have left my brain

Thanks again!
dh

---

### Post by digitalhillbilly on 2007-10-17
Solved! I will mark the title solved as well, as soon as I figure out how to anyway.

The thread I was looking for is: [http://ubuntuforums.org/showthread.php?t=323939](http://ubuntuforums.org/showthread.php?t=323939)

Which also points to these two great docs: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)  and
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

Thanks!
dh

---

### Post by DagMan on 2007-10-17
I'll use Firefox as the example package here

to get the source code from ubuntu repos, you need lines in your sources.list that say ```
deb-src
``` as well as just ```
deb
```, so one deb-src corresponding to each deb line.  This get's info about what's available from the source repo when you apt-get update. Then after updating.
```
apt-get source firefox
```
Ideally, software requirements to build are pulled in by this
```
apt-get build-dep firefox
```
Then to look at the configure options
```
./configure --help
```
At this point you can also try to take a look at what options were used to build the original file in the debian directory and usuall in the rules file.  so for example while inside the first level of the package folder
```
gedit debian/rules
```This can get confusing to look at and not all packages are created equally, but if you want to change a few values in there then you can give it a go and see if the build fails or not.  I don't recompile much but on occasion I'll want to change the CFLAGS or add in support for something and on rare occasion remove support for something, in the ./configure options.  Another place to look for CFLAGS and CXXFLAGS is in the Makefile because it looks a bit patched when apt-getting the source.

From here you can ususally build the package as root from the main directory of the package by doing this 
```
debian/rules binary
```but again not all packages are created equal.

More on inequality, it seems that sometimes **apt-get build-dep** doesn't actually get all the needed build dependencies.

This described above isn't actually the greatest way to do things however it will work often.  Also, there is a package called prevu that is meant for backporting things for example if you run feisty and want to try to build something from gutsy that is not available in feisty then you can run it and it attempts to set up a clean chroot environment and only install what it needs for each package removing the build dependencies when its done so that there aren't conflicts later on.  It can easly be set up to build a feisty package for feisty, for example, but your're just rebuilding the same build that's in the repos, so hacking at the prevu script so that it stops just before building and lets you edit said files is worth looking into.  I had that set up a long time ago but in the end it's just not worth it and aside from the actual kernel itself sitting there alaways running with the proccesor type compiled to less than a pentium pro, I've in the past always been annoyed and had to recompile but I don't think prevu is the best thing for this.

Okay so as for the first part, you don't have to build using the debian/rules file but it's good to still look at it to see what's been enabled in the official build so you don't miss something you hadn't thought of.  You can, and this is actually not recomended because you might end up building to a differant location, and in the debian folder you may also see that when you build the way it was built for ubuntu there's sometimes many, many other things there that are patches for making things fit together overall or because something just might not build without those things.  If you just want to run ./configure --help then you can look at the options, then run
```
./configure --various --options --go --here
make

```
and now if it doesn't exit with an error, you can do this 
```
sudo make install
```
but better is to get the package checkinstall and use it instead of make install
```
sudo apt-get checkinstall
```
and instead of the sudo make install use
```
sudo make checkinstal
```l
or maybe it's just
```
sudo checkinstall
```  I don't remember now.
Checkinstall builds a .deb package that you install using dpkg
so ```
dpkg -i packagename.deb
```
and the advantage here is that apt now knows about it and how to uninstall it ...and so does synaptic, where you might otherwise be stuck with a binary on your system and end up with multiple binaries of the same thing which can confuse things for the OS and for you.... for the OS because of the crap in crap out principle though.

The second part is the way to go for compiling things outside of the repo though you may have a little sluething to do in meeting the build dependancies... they are usually in the repos by the way, the build dependancies, but not always the same exact name that the package asks for when it's nice enough to fail and explicitly say what is missing.

---

### Post by DagMan on 2007-10-17
BARG... all that typing.  I knew it would happen to.
Thanks for adding solved to the subject and also for the links :)

---

### Post by digitalhillbilly on 2007-10-17
lol! Isn't that always the case eh? Your typing did not go to waste though. Hearing something explained through the words of a few people really goes a long way. For myself and anyone else that searches out this same topic.

> ...I don't recompile much but on occasion I'll want to change the CFLAGS or add in support for something and on rare occasion remove support for something...

My case exactly. I don't often do it but sometimes it's needed. Today I'm building Gephex (gephex.org) and it works best if ffmpeg is compiled from the latest checkout to alleviate some funk - the last latest i used was 3 months ago and it worked like a charm so I'm hoping the *latest* latest works as well.

Thanks for your help!
dh

---

