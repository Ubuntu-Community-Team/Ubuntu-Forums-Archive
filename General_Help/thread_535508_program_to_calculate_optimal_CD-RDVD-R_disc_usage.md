---
title: "program to calculate optimal CD-R/DVD-R disc usage?"
date: 2007-08-26
forum: General Help
---

### Post by MustNotSleep on 2007-08-26
heya! been using Feisty for a few weeks now, and things have been smooth for the most part. i'm a recent Windows "switcher", though i've had previous experiences with *nix (RH, Debian, Slackware, PCLinuxOS, OSX), so i'm not as green with the whole system, though i'm still an all-around beginner. that said, i find myself much more satisfied with my Ubuntu install than my not-so-recent Vista upgrade, and end up using (and wanting to use it) more.

anyways, from time to time i come across the need to use a certain program i've taken for granted on Windows, but can't find a suitable alternative in Linux.

case in point: i used a small, poorly coded, freeware program called [SizeMe]("http://lars.werner.no/wordpress/?page_id=2") to calculate the most optimal size of a selected directory in order to completely fill a burnt DVD or CD. basically, you feed it a path and it gives you a structure of discs based on the size you select (4482mb, 700mb, etc.). then you could simply drag and drop the file list into your favorite data burning app and off you went.

i do this because i continually deal with small to medium sized files (yes, PORN! :p) and ocasionaly the directory i archive them in overflows the data limit of a DVD-R. then it becomes a PITA to manually pick and match the best file selection in order to optimally fill the disc.

i've been googling for a while for this, but i really don't know what to look for.

and i've secretly been hoping that, if possible, someone shell-savvy enough could cook me up a pipe'd and regex'd command that would solve my problems, without the need to recur to a separate GUI application. because -- let's face it -- if there's something Unix is famous for is simplifying automated tasks that would be difficult or impossible on other systems by the use of a few well-formulated shell commands. and being the CLI-newb that i am, i simply have no idea how to pull this off.

any help or suggestion is much appreciated, guys and girls... you've got an awesome forum here! :)

---

### Post by chrome307 on 2007-08-26
I maybe missing the point here somewhere ........ but doesn't a native burning application just give you a visual guide to show you how much your using to make your compilation and this is usually a timeline of sorts.

If that's of any use, then K3b is a burning application that has this feature.

---

### Post by MustNotSleep on 2007-08-26
> **chrome307 said:**
> I maybe missing the point here somewhere ........ but doesn't a native burning application just give you a visual guide to show you how much your using to make your compilation and this is usually a timeline of sorts.

If that's of any use, then K3b is a burning application that has this feature.
indeed. any burning app does that. that's not what i'm trying to achieve.

what i want is a program that takes two inputs: a directory and a template (DVD/CD, etc.), and have it output **how many** discs it would take to burn all the contents in that directory based on the template i chose, filling the discs to the brim.

oh i just remembered! [Burn To The Brim](http://sourceforge.net/projects/bttb/) is another Windows utility i used for this, but can't remember why i stuck with SizeMe after all..

basically the output could be similar to this:

```
Disc1 -- (99%) [4,479MiB]
Directory
|
+--- Dir1
+--- File1

Disc2 -- (98%) [4,468MiB]
Directory
|
+--- Dir2
+--- File2

Disc3 -- (45%) [2,130MiB]
|
+--- Dir3

etc...
```
check out the apps i mentioned and their description, they explain it much better than i do.

btw, i checked out K3b out of curiosity, and it doesn't seem to do what i need. it's just another run-of-the-mill burning app.

anyone else?

---

### Post by largie on 2007-09-09
MustNotSleep:

As the author of SizeMe I wonder why it is poorly coded? It gets the job done right?

Any suggestions to make it better is always welcome! :popcorn:

---

### Post by MustNotSleep on 2007-09-09
> **largie said:**
> MustNotSleep:

As the author of SizeMe I wonder why it is poorly coded? It gets the job done right?

Any suggestions to make it better is always welcome! :popcorn:
heh, sorry... this is awkward... :D

this would be considered off-topic, but let's just say that it's crashed a couple of times, and the UI is somewhat odd-looking.. but maybe i'm just spoiled with Vista's fisher-price eye-candy (which is another thing: it doesn't support Vista's Aero interface).. it hasn't been updated since 2005, so i suppose i can't expect much (using version 2.0.0).. also, that "Make a donation" button in the title bar is a bit too much, IMHO..

but hey, don't mind me, i'm just nitpicking.. your program is certainly the best choice for this type of thing.. and since i moved to Linux, i'm looking for something similar.. do you have an idea?

---

### Post by largie on 2007-09-12
Well, if it crashed then a crashreport should be sendt to me. Almost every CP-entry I got is from Win98 crashin' and but that is unsupported now.

There migth be some bugs in the threadingmodel (been a while since I programmed it). And sure it hasn't been updated, since there hasn't been much response on it after 2.0 came out. The time for programming was radically reduced when I was finished with school.

Now I got a new job who gives me alot of spare time, therefore I would might update SizeMe to 3.0. It will include some bugfixes, filelist-reports (99% finished), cd/dvd cover printing (30% finished) and the backup feature (80% finished).

As for the UI, it is a little different cause I wanted it to be. Users shouldn't rate the software based on it looks but it is almost done every time.

Linux does have alot of utils, and I got the idea from a simple script we had @ school. But no GUI or anything like that. I would suggest that you use a backup-tool or simular.

---

### Post by ljw1 on 2007-12-30
The programs I am using at the moment to do this task is gaffitter and k3b. It works the same for me as sizeme and nero. You will need to get the gaffitter to k3b script as well to pass the filenames and make sure you have k3b open before you run the script as it did strange things if it was not open. If you get stuck let me know.

---

### Post by stinger30au on 2008-04-21
> **ljw1 said:**
> The programs I am using at the moment to do this task is gaffitter and k3b. It works the same for me as sizeme and nero. You will need to get the gaffitter to k3b script as well to pass the filenames and make sure you have k3b open before you run the script as it did strange things if it was not open. If you get stuck let me know.

i know this is an old thread, but this is exactly what i need. can someone please explain in *SIMPLE terms how to get this up and running. i have got k3b installed, how do i install and configure gaffitter????

---

### Post by stinger30au on 2008-04-21
Size me verison 2 does work in Ubuntu.... with a twist.

grab the software here
[http://lars.werner.no/?page_id=2](http://lars.werner.no/?page_id=2)
install it in wine.

create a spare directory on a hdd somewhere that has enough spare space to save enough data to fill a dvd, say 4.4 gig.
call the directory for example 

sizeme-output

now, fireup sizeme and point it to the directory you need sized up.

when it makes the cd listing in green, click on disc one and then right click on it and select "copy to"
point it to the directory you just created.
it will copy these files to that directory.
now fireup K3b or whatever and tell it to make a new dvd complilation and copy/paste the files from the sizeme-output directory to the K3B layout and burn away.
do this for each disc.
a little time consuming, but it works!!!
hooray for me!!!

---

### Post by MustNotSleep on 2008-04-21
thanks to the suggestions in this thread, i've found gaffitter fits my needs perfectly..

the command i use to calculate a DVD-R worth of data is:

gaffitter -t 4482 -m --bs 2048 *

i don't use k3b for burning, but it would be trivial to make a simple bash script that moves the necessary files into their respective directories to make the process easier.. this is on my todo list as soon as i have some free time.. :)

---

### Post by stinger30au on 2008-05-17
i have upgraded  to Ubuntu 8.04 and sizeme v 2 will install, but when i try and run it, the hard drive flashes for a few seconds then stops and the program does not appear on my desktop :-((

---

### Post by stinger30au on 2008-05-17
after some hunting i have found a windows program that may do the trick. 
its called fillcd

version 3 is shareware and version 2 is freeware
the software was written by a "Tim Russel"
 the official web site is

[http://www.fillcd.com/](http://www.fillcd.com/)

but it looks like it has been replaced
im trying to find a site that hosts the version 2 freeware version
after some searching i found it
[ftp://ftp.sunet.se/pub/pc/mirror/simtelnet/win95/diskutl/fillcd20.exe](ftp://ftp.sunet.se/pub/pc/mirror/simtelnet/win95/diskutl/fillcd20.exe)

---

### Post by stinger30au on 2008-06-09
gaffitter a native linux app has been updated to run via nautilus scripts

[http://gaffitter.sourceforge.net/#toc5](http://gaffitter.sourceforge.net/#toc5)

the program gaffitter is in the ubuntu repos

---

### Post by lisati on 2008-06-09
Another Windows program I'm aware of is MyDVD from Sonic (Roxio???) - the version that came preinstalled on my Compaq desktop has an option for data archiving which does a similar job.

---

### Post by stinger30au on 2008-07-04
> **stinger30au said:**
> i have upgraded  to Ubuntu 8.04 and sizeme v 2 will install, but when i try and run it, the hard drive flashes for a few seconds then stops and the program does not appear on my desktop :-(


there is a cure for this thanks to the efforts at wine hq

Looks like that app forgot to bundle two important runtime libraries. 
The fix is 

(copy and paste each line to a shell command line)

wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
sh winetricks vcrun6 

The app starts ok for me then.

---

