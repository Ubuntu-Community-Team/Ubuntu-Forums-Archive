---
title: "convert avi to dvd?"
date: 2007-01-12
forum: General Help
---

### Post by haxer on 2007-01-12
Hello i have some .avi files i want to convert it to dvd so i can burn it as an dvd/isodvd is it possible? :-k

---

### Post by haxer on 2007-01-12
anyone? :-k

---

### Post by NeoLithium on 2007-01-12
You bet; I use avidemux.  All you have to do is select the DVD option and save the file; it'll convert it nicely for you.

---

### Post by haxer on 2007-01-12
avidemux is it in the repos or how to get it? :-k

---

### Post by NeoLithium on 2007-01-12
Yep, it's in the repos:
```
sudo aptitude install avidemux
```

---

### Post by haxer on 2007-01-12
THX :) ill try it sounds good :D

---

### Post by ~LoKe on 2007-01-12
I prefer the command line, but it's really up to you.

[http://movabletripe.com/archive/merging-avis-into-a-single-dvd-on-linux/](http://movabletripe.com/archive/merging-avis-into-a-single-dvd-on-linux/)

Just skip the part about concatenating and syncing avi's.

**EDIT:** But with this, you won't have any menu's.

---

### Post by kebes on 2007-01-12
What I use is the "tovid" commandline tool to conveniently transform any .avi into .mpg, then I use "dvdauthor" and "growisofs" to burn it to disk. It can all be automated quite conveniently.

Thus I first run something like:
```

tovid -in FILE_TO_CONVERT -out OUTPUT_FILENAME

```

Then I run this script:

```

#!/bin/bash
#############################################################
#
# Writes all local *.mpg files to DVD. The script will burn
# any local *.mpg file, in alphanumeric order.
#
#############################################################

# Temporary directory based on PID
WORKDIR=work$$

# Process all local mpeg files
cmd="ls --format=horizontal -tr *.mpg"
FILES=`$cmd`

echo "Will process "
echo $FILES

# Make a DVD filesystem based on the mpeg file
dvdauthor -o $WORKDIR $FILES
dvdauthor -o $WORKDIR -T
# Burn DVD filesystem
growisofs -dvd-video -Z /dev/dvd $WORKDIR

# Clean up
rm -r $WORKDIR

```

---

### Post by haxer on 2007-01-13
Ok what is the easiest way this app named avidemux was really hard to get anything about anyone else with the easiest way? :-k  Command line looked nice but sounds hard.

---

### Post by kebes on 2007-01-13
> **haxer said:**
> Ok what is the easiest way this app named avidemux was really hard to get anything about anyone else with the easiest way? :-k  Command line looked nice but sounds hard.

If you want to do it in a purely GUI way, then I think you'll have to use a combination of programs (I'm not aware of a single program that does it all). So you would start with avidemux to convert from avi to mpg. Then use, for example, the [KDE DVD Authoring Wizard]("http://dvdauthorwizard.sourceforge.net/view.php/page/Voorpagina") to prep the dvd filesystem. Then you can burn to disk using K3B. (Actually apparently the authoring wizard can activate K3B automatically.)

Alternately there's a program called [DeVeDe]("http://www.rastersoft.com/programas/devede.html") that seems to be a GUI frontend for the mencoder and dvdauthor commandline tools. I've never used it so I don't know how good it is.



I personally use the commandline way... yes it's confusing to install/use at first, but once you know the basics, it's very efficient. (And it can easily be automated, which I like...) If you want to go that route you have to manually install [tovid]("http://tovid.wikia.com/wiki/Main_Page"). But it's not that hard because the [installation page]("http://tovid.wikia.com/wiki/Installing_tovid") provides an [Ubuntu package]("http://tovid.sourceforge.net/download/ubuntu/") and [detailed instructions]("http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu").

You can lots of fancy things with tovid, and sometimes you may need to manually set aspect ratio, but basically the command is just:
tovid -in input.avi -out output.mpg

After that, you can use "dvdauthor" to create a dvd filesystem, and "growisofs" to burn it to DVD. (Or you can use your GUI dvd burner to select the image and burn it to disk if you prefer.)

Feel free to ask questions about the commandline tools if you need help with it.

---

### Post by haxer on 2007-01-13
Ok the command line tools for .avi to dvd the easiest way nice if i could get it in .isodvd if its possible :) ;) :-k

lets say i have 

home/haxer/Desktop/downloads/movies/avi  then the file undisputed.avi and then convert it to dvd or dvdiso and save it in home/haxer/Desktop/downloads/movie/dvdrip =?

---

### Post by kebes on 2007-01-13
1. Install tovid using the provided Ubuntu package:
[http://tovid.wikia.com/wiki/Installing_tovid](http://tovid.wikia.com/wiki/Installing_tovid)
(You can do all this without tovid but tovid makes it much easier.)
During install it may complain that you need other things installed, for example "mplayer". Just install those with your Synaptic package manager (Applications > Add Applications) or on the commandline by doing:
sudo aptitude install mplayer

You will also need to install "dvdauthor" and "growisofs", either using Synaptic, or on the commandline:
sudo aptitude install dvdauthor
sudo aptitude install growisofs


2. Once tovid is installed, open up a terminal (Applications > Accessories > Terminal) and navigate to the directory in question:
```

cd /home/haxer/Desktop/downloads/movies/

```

(Hint: when typing out the above command, you can hit "TAB" to have the shell autocomplete long names... so just type "cd /ho" and then hit "TAB" and it will complete it as "cd /home/" and then type "ha" and hit "TAB" again... it makes it easier to navigate!)

After hitting enter, you'll be in the right directory. You can list available .avi files by typing:
```
ls *.avi
```

3. To convert a specific file, just go:
```
tovid -in undisputed.avi -out undisputed.mpg
```

Then move this file to the other directory where you want it:
```
mv undisputed.mpg ../dvdrip/
```

(The "../" means "go up to parent directory".)

Then switch to this other directory:
```
cd ../dvdrip/
```

4. Now convert the mpeg file into a DVD filesystem:
```
mkdir newdvd
dvdauthor -o newdvd undisputed.mpg
dvdauthor -o newdvd -T
```

The first command creates a new temporary directory.
The second command takes your new MPEG file and creates a DVD filesystem.
The third command creates a table-of-contents for your new DVD.

5. Now you can burn your DVD:
```
growisofs -dvd-video -Z /dev/dvd newdvd
```

Instead of using "growisofs" you can use whatever GUI burning program, if you prefer. The "filesystem" will not be in a single ISO file but rather will have the standard DVD-video directories. Most DVD-burning programs will recognize this and burn it properly. The "growisofs" command will burn it properly.



Okay, I admit all those commands look complicated... of course for many of those steps (making directories, moving files) you can use your file browser if you prefer. I hope my explanations make sense. If not, or if you get stuck, feel free to ask questions.

---

### Post by haxer on 2007-01-14
Thx this way looks fine but hard untill i learn :)

---

### Post by nix4me on 2007-01-14
Devede works very nicely.

nix4me

---

### Post by neoroses on 2007-01-14
r33t guys i seriously recommend using DEVEDE [http://www.rastersoft.com/programas/devede.html]("http://www.rastersoft.com/programas/devede.html") ..you need to get a few dependencies but if you dont have them it tells you what u need to get so when it does just use 

```
sudo apt-get install (insert here what it says you need)
```

then you can save your avi files as a dvd image, bin and cue or even as compliant MPGS

simple :)

---

### Post by haxer on 2007-01-14
Ok is it really that simple? :-k ;)

---

### Post by ardchoille42 on 2007-01-14
All I had to do was install Mplayer, Mencoder, DVDAuthor, VCDImager and then Devede ran fine.

---

### Post by neoroses on 2007-01-14
yea man..its an amazing peice of software it is seriusly simple and easy to use......i hate to say it but its just as easy  as it is to do in windows

---

### Post by haxer on 2007-01-14
hahaha.. ok ive downloaded it will  get in to it tomorrow ;)

---

### Post by nix4me on 2007-01-14
I've made about 10 dvds with devede.  They all work perfectly.

nix4me

---

### Post by Doug11 on 2007-01-14
I use Devede as well. I just create a disc structure,,and then burn the structure with K3b. Works great.

---

### Post by wxnker on 2007-02-18
One more DeVeDe user. It's a great program. Nothing wrong with doing it the command line way but as I see it I'd rather keep it simple if possible. DeVeDe does it all for you. :D
For the novice/regular user Linux is a much stronger and more attractive alternative to Windows if we keep it simple, when possible.

---

### Post by gaspard.leon on 2008-07-15
Digging up an old thread...

I have been using DeVeDe with much success, however...

I just today noticed that DeVeDe only supports max 12 titles...

arrgh

I have been tasked with compiling 50 video clips in .mp4 and .mov formats into a DVD where you can select them by name...

So DeVeDe is not quite sufficient as it can only _NAME_ 12 items, I can have like 6 categories and put the files under those, but it's not usable as the items need names.

So I started using the tovid GUI to assemble it... (it supports multi-level menus) but it's a bit messy and crashed while I was using it, and it doesn't do save, (I'll be trying again tonight tho)...

So I'm also going to try KDE DVD Authoring Wizard... does anyone know what it's limits are (for titles etc?)

Also does it have a forum or something?

Also does it do the transcoding?

If not, anyone know a GUI tool (or front-end for a CLI tool) that does batch transcodes... I could do them 1 by 1 but there are 3 discs with 50 files each for 150 files...

Cheers,

Gaspard

---

### Post by MaiKeth on 2008-07-16
Theres also ManDVD [http://www.getdeb.net/app.php?name=mandvd](http://www.getdeb.net/app.php?name=mandvd)
It's like DeVeDe

---

### Post by imon9 on 2008-07-16
use ManDVD

[http://www.getdeb.net/app/ManDVD](http://www.getdeb.net/app/ManDVD)

---

### Post by dchurch24 on 2008-07-20
> **kebes said:**
> What I use is the "tovid" commandline tool to conveniently transform any .avi into .mpg, then I use "dvdauthor" and "growisofs" to burn it to disk. It can all be automated quite conveniently.


I know it's an old thread, but that script is VERY useful.

Just wanted to say thank you - it's exactly what I was after.

---

