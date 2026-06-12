---
title: "random welcome message when logging in, help!"
date: 2006-11-26
forum: General Help
---

### Post by patagonik on 2006-11-26
Hy!

I've been wondering :-k  if it's possible to create a script that periodically, like every day, or every time you log in / log out ubuntu, automatically takes one file in a folder and renames it with a specific name. I'm sure this  could be quite simple to do, but i have no idea about programming or anything similar... can anyone give me a clue about how to do it or where to look for some more information? 

The point of this script could be to change the name of a randomly selected sound file between a list of files contained in a certain folder so each time that ubuntu starts, the Log In sound will be different, lets say for example, sound recorded from festival saying "Welcome Mr. Ubunter" or "How is everything going today Mr. Ubunter" or "What's up dude?" or whatever... of course the same could (and should) be done for the Log Out sound. By doing this you'll avoid excessive repetitiveness in the "metalic" voice of your  computer saying hello or good bye!

That's my idea, which i can't develop alone. Someone?

Thanks in advance guys!

pata

---

### Post by patagonik on 2006-11-27
Now seriously... nobody? Please help!!! Please, please, please!!!!

---

### Post by taurus on 2006-11-27
Look in /etc/init.d/bootmisc.sh!!!

```

#       Update /etc/motd. If it's a symbolic link, do the actual work
#       in the directory the link points to.
#
if [ "$EDITMOTD" != no ]
then
        MOTD="`readlink -f /etc/motd || :`"
        if [ "$MOTD" != "" ]
        then
                uname -a > $MOTD.tmp
                sed 1d $MOTD >> $MOTD.tmp
                mv $MOTD.tmp $MOTD
        fi
fi

```

p.s. Hmm...  You are talking about sound, not MOTD!!!

---

### Post by patagonik on 2006-11-27
In wikipedia i've found that: MOTD can refer to:

    * a computer acronym that stands for Message Of The Day. A MOTD is a text file displayed to a user logging in on IRC, a shell using telnet or SSH, or FTP. The MOTD is typically used to display rules, administrator contact, or simply a piece of ASCII art.

But i don't wanna display a text, but a sound as you said. I'll try to understand how that little script you've posted works. 

Thanks a lot anyway! Some starting point should be the firstone!

pata

---

### Post by frafu on 2006-12-01
I am not a scripter, but this might help: 
[http://freeos.com/guides/lsst/](http://freeos.com/guides/lsst/)

---

### Post by patagonik on 2006-12-01
perfecto!!!

---

### Post by hartz on 2007-01-27
If the original asker still wants this, I can help.  I just did something similar.

My script picks 4 .JPG files at random from a directory containing 2512 Wallpaper images.  It then creates a Mozaic of thos images, and saves the output to a .PNG file which is used as my desktop wallpaper.

---

### Post by KIAaze on 2007-03-21
> **hartz3 said:**
> If the original asker still wants this, I can help.  I just did something similar.

My script picks 4 .JPG files at random from a directory containing 2512 Wallpaper images.  It then creates a Mozaic of thos images, and saves the output to a .PNG file which is used as my desktop wallpaper.

Post it! Scripts are always wanted. :)
Especially if you manage to make a mosaic of 4 pictures! :O
I suppose you use a special program for this, because I can't see how to do that purely in shellscript. ^^

This sounds like a fun script to write, I'll try doing it.
I already found those helpful little script bits:

getting random numbers:

```
#!/bin/sh

RANDOM=`date '+%s'` #seed initialization
echo $[($RANDOM % 60) + 1]
echo $[($RANDOM % 60) + 1]
echo $[($RANDOM % 60) + 1]

```

```
echo $RANDOM
```

renaming files oldfile.* into newfile
 sh, ksh, or bash:

```
for file in oldfile.*
do
   newname=`echo $file | sed -e 's/oldfile/newfile/'`
   mv $file $newname
done

```
csh or tcsh:

```
#!/usr/local/bin/tcsh
foreach file (oldfile.*)
   set newname=`echo $file | sed -e 's/oldfile/newfile/'`
   mv $file $newname
end

```

(usually the shell is bash by default)

---

### Post by mcduck on 2007-03-21
> **KIAaze said:**
> 
Especially if you manage to make a mosaic of 4 pictures! :O
I suppose you use a special program for this, because I can't see how to do that purely in shellscript.Piece of cake. Just install Imagemagick, it can handle pretty much an image processing task you can imagine and it's a CLI tool so it's easy to use it in scripts ;)

edit: following code would create array of 4 pictures and then resize it to 1024x768
```
convert \( pic1.png pic2.png +append \) \( pic3.png pic4.png +append \) -append -resize 1024x768 wallpaper.png
```

other way to get the same result would be this:
```
montage pic1.png pic2.png pic3.png pic4.png -geometry +0+0 -tile 2x2 -resize 512x384  wallpaper.png
```

---

### Post by hartz on 2007-03-27
As suggested by previous posters, my script uses montage, which is part of the imagemagick "package".  One day I'd like to turn the script into something useful, for example by making it set a new desktop wallpaper image and then informing the desktop manager that the image needs to be reloaded from the file.

This script was as much a learning experience as an experiment.  For me, shell scripting is something of a hobby - I love writing miscellaneous odd occasionally even useful scripts.

```

#!/bin/sh

# Script to generate a 4x4 montage of some randomly selected images.
# Known problems:
# - sometimes the same image can appear more than once in the same script.
# - The constants needs to be turned into command-line arguments/options

# The $RANDOM shell special variable will generate a number in the 
# range 0 .. MAXINT on every reference.  We need a function which 
# will select a number in the range 0 .. NR-of-files.  This 
# function takes as argument the numeric value for Nr Of files
# and then emits a number between 0 and "nr-of-files"
MyRandom() 
{
RNUM=$RANDOM
D=$(( $RNUM/$1 ))
X=$(( $1*$D ))
echo $(( $RNUM-$X ))
}

# Set up some constants
# PICTDIR is the directory where we want the script to search for image files
PICTDIR=~/MyDownloads/sexy

# OUTPUTFILE is the name of the image to be written to disk on completion
OUTPUTFILE=~/montage4x4.png

# PICTLIST is a temporary file which will be a text file containing a list 
# of the images to choose from
PICTLIST=/tmp/picturelist.$$

# Set VERBOSE to "on" to make the script emit some output
VERBOSE=on

# If "DISPLAYPICT" is set to "on", the script will run the program specified 
# by "IMAGEVIEWER" to display the montage output result
DISPLAYPICT="on"
IMAGEVIEWER=/usr/bin/eog

# We need to do two things: Generate a text file containing a list of 
# all the picture files that we have available, and determine the number 
# of files.  Both of those things are accomplished by this line
NROFPICS=$( find $PICTDIR  -name "*jpg" | grep -v "/\." | tee $PICTLIST | wc -l )

# Now we select 4 of those pictures at "random".  I used sed just to 
# be fancy.  You could use awk or a combination of head and tail.
PIC1=$( sed -n "$( MyRandom $NROFPICS ) p" $PICTLIST )
PIC2=$( sed -n "$( MyRandom $NROFPICS ) p" $PICTLIST )
PIC3=$( sed -n "$( MyRandom $NROFPICS ) p" $PICTLIST )
PIC4=$( sed -n "$( MyRandom $NROFPICS ) p" $PICTLIST )

if [ $VERBOSE = "on" ]
then
   echo Found $NROFPICS in Source dir $PICTDIR ...
   echo Selected Pictures:
   echo 1: $PIC1
   echo 2: $PIC2
   echo 3: $PIC3
   echo 4: $PIC4
fi

[ $VERBOSE = "on" ] && echo -n "Generating montage ..."

# See the montage command man page for usage instructions - it can do 
# some realy fancy stuff beyond what I am using here.
montage -gravity center -geometry 1200x1200\> -shadow $PIC1 $PIC2 $PIC3 $PIC4 $OUTPUTFILE

if [ $VERBOSE = "on" ]
then
   echo
   ls -l $OUTPUTFILE
   file $OUTPUTFILE
fi

[ $DISPLAYPICT = "on" ] && $IMAGEVIEWER $OUTPUTFILE


```

---

### Post by KIAaze on 2007-04-05
I still haven't made a script doing it, but found something even more interesting:
> Change Wallpaper from Gnome Hacks : This one can use a random image from a folder you specify or **download random wallpapers on the fly from the art.gnome.org website** and use that, or specify a folder full of images. You can add the script to be run at session startup.
[http://ubuntu.wordpress.com/2005/12/01/random-wallpaper-in-gnome/]("http://ubuntu.wordpress.com/2005/12/01/random-wallpaper-in-gnome/")
:)

And thanks to hartz3  for his script. :)

---

### Post by airtonix on 2007-05-11
dude go back to the second post and use that method combined with fesitival.

get it to rad your text files....

less storage space required

surprisngly not much cpu required either

also : 

> sudo apt-get install festival gaim-festivalthis will make gaim speak your im msg to you!

edit : forgot that after you install gaim-festival you need to enable it like other gaim plugins.

im using it now and im falbbergahsted.......its soooooo coool.

---

### Post by hartz on 2007-05-12
I think you have a small typo in that command.  The last bit that reads "gaim-festival" should read "festival-gaim"

---

### Post by sv452 on 2007-10-30
hi all ...

so i tried to run the script for the wallpaper montage by hartz and the thing is when i have only 4 pics in dir it works more than that i get errors ...

> 

wallpaper: 47: arithmetic expression: syntax error: " /180 "
wallpaper: 48: arithmetic expression: syntax error: " /180 "
wallpaper: 49: arithmetic expression: syntax error: " /180 "
wallpaper: 50: arithmetic expression: syntax error: " /180 "
Found 180 in Source dir /home/sv452/Pictures/pics/misc ...
Selected Pictures:
1: /home/sv452/Pictures/pics/misc/hair2.jpg /home/sv452/Pictures/pics/misc/wheat.jpg /home/sv452/Pictures/pics/misc/rose05.jpg /home/sv452/Pictures/pics/misc/legs.jpg /home/sv452/Pictures/pics/misc/trio.jpg /home/sv452/Pictures/pics/misc/play_with_me.jpg /home/sv452/Pictures/pics/misc/touch2.jpg /home/sv452/Pictures/pics/misc/sex_no.jpg /home/sv452/Pictures/pics/misc/pub.jpg /home/sv452/Pictures/pics/misc/honey.jpg /home/sv452/Pictures/pics/misc/hot.jpg /home/sv452/Pictures/pics/misc/dog.jpg /home/sv452/Pictures/pics/misc/plumage.jpg /home/sv452/Pictures/pics/misc/tub.jpg /home/sv452/Pictures/pics/misc/candy.jpg /home/sv452/Pictures/pics/misc/squat.jpg /home/sv452/Pictures/pics/misc/tube.jpg /home/sv452/Pictures/pics/misc/ass4.jpg /home/sv452/Pictures/pics/misc/gum.jpg /home/sv452/Pictures/pics/misc/nun.jpg /home/sv452/Pictures/pics/misc/baby.jpg /home/sv452/Pictures/pics/misc/hat.jpg /home/sv452/Pictures/pics/misc/screw.jpg /home/sv452/Pictures/pics/misc/fan.jpg /home/sv452/Pictures/pics/misc/rose6.jpg /home/sv452/Pictures/pics/misc/wedding.jpg /home/sv452/Pictures/pics/misc/blond.jpg /home/sv452/Pictures/pics/misc/body.jpg /home/sv452/Pictures/pics/misc/bride2.jpg /home/sv452/Pictures/pics/misc/sunrise.jpg /home/sv452/Pictures/pics/misc/4bm.jpg /home/sv452/Pictures/pics/misc/stages.jpg /home/sv452/Pictures/pics/misc/caviar.jpg /home/sv452/Pictures/pics/misc/twins.jpg /home/sv452/Pictures/pics/misc/table.jpg /home/sv452/Pictures/pics/misc/dick.jpg /home/sv452/Pictures/pics/misc/balls.jpg /home/sv452/Pictures/pics/misc/dinner.jpg /home/sv452/Pictures/pics/misc/gap.jpg /home/sv452/Pictures/pics/misc/smoke2.jpg /home/sv452/Pictures/pics/misc/housemaid.jpg /home/sv452/Pictures/pics/misc/pink.jpg /home/sv452/Pictures/pics/misc/band.jpg /home/sv452/Pictures/pics/misc/uzi.jpg /home/sv452/Pictures/pics/misc/sink.jpg /home/sv452/Pictures/pics/misc/cow.jpg /home/sv452/Pictures/pics/misc/dolphin.jpg /home/sv452/Pictures/pics/misc/merrymas_newyear.jpg /home/sv452/Pictures/pics/misc/cheers.jpg /home/sv452/Pictures/pics/misc/heel.jpg /home/sv452/Pictures/pics/misc/chair.jpg /home/sv452/Pictures/pics/misc/cool.jpg /home/sv452/Pictures/pics/misc/kiss.jpg /home/sv452/Pictures/pics/misc/bubbles.jpg /home/sv452/Pictures/pics/misc/twins2.jpg /home/sv452/Pictures/pics/misc/cigarette.jpg /home/sv452/Pictures/pics/misc/ubuntu.jpg /home/sv452/Pictures/pics/misc/cork.jpg /home/sv452/Pictures/pics/misc/catch.jpg /home/sv452/Pictures/pics/misc/sleeping.jpg /home/sv452/Pictures/pics/misc/retro.jpg /home/sv452/Pictures/pics/misc/in_my_corner.jpg /home/sv452/Pictures/pics/misc/bear.jpg /home/sv452/Pictures/pics/misc/feather2.jpg /home/sv452/Pictures/pics/misc/army_boots.jpg /home/sv452/Pictures/pics/misc/wine.jpg /home/sv452/Pictures/pics/misc/summer.jpg /home/sv452/Pictures/pics/misc/strawberry.jpg /home/sv452/Pictures/pics/misc/tit.jpg /home/sv452/Pictures/pics/misc/touch.jpg /home/sv452/Pictures/pics/misc/mirror2.jpg /home/sv452/Pictures/pics/misc/snejina02.jpg /home/sv452/Pictures/pics/misc/merry_xmas.jpg /home/sv452/Pictures/pics/misc/chanel.jpg /home/sv452/Pictures/pics/misc/dock_girl.jpg /home/sv452/Pictures/pics/misc/scratching.jpg /home/sv452/Pictures/pics/misc/back.jpg /home/sv452/Pictures/pics/misc/cumshot.jpg /home/sv452/Pictures/pics/misc/police.jpg /home/sv452/Pictures/pics/misc/take_off.jpg /home/sv452/Pictures/pics/misc/group.jpg /home/sv452/Pictures/pics/misc/come.jpg /home/sv452/Pictures/pics/misc/ann_angel.jpg /home/sv452/Pictures/pics/misc/smoke.jpg /home/sv452/Pictures/pics/misc/paint2.jpg /home/sv452/Pictures/pics/misc/socks2.jpg /home/sv452/Pictures/pics/misc/olive.jpg /home/sv452/Pictures/pics/misc/blowjob2.jpg /home/sv452/Pictures/pics/misc/ice2.jpg /home/sv452/Pictures/pics/misc/perfect_angel.jpg /home/sv452/Pictures/pics/misc/rose.jpg /home/sv452/Pictures/pics/misc/candles.jpg /home/sv452/Pictures/pics/misc/blowjob.jpg /home/sv452/Pictures/pics/misc/scratch.jpg /home/sv452/Pictures/pics/misc/garden.jpg /home/sv452/Pictures/pics/misc/shower.jpg /home/sv452/Pictures/pics/misc/daobg.jpg /home/sv452/Pictures/pics/misc/squeeze.jpg /home/sv452/Pictures/pics/misc/pussy2.jpg /home/sv452/Pictures/pics/misc/spaghetti.jpg /home/sv452/Pictures/pics/misc/o.jpg /home/sv452/Pictures/pics/misc/autumn.jpg /home/sv452/Pictures/pics/misc/shark_girl.jpg /home/sv452/Pictures/pics/misc/dirty.jpg /home/sv452/Pictures/pics/misc/violin.jpg /home/sv452/Pictures/pics/misc/ussr.jpg /home/sv452/Pictures/pics/misc/dita.jpg /home/sv452/Pictures/pics/misc/wet.jpg /home/sv452/Pictures/pics/misc/wet2.jpg /home/sv452/Pictures/pics/misc/Gorgona_Meduza.jpg /home/sv452/Pictures/pics/misc/look.jpg /home/sv452/Pictures/pics/misc/rope.jpg /home/sv452/Pictures/pics/misc/cherry.jpg /home/sv452/Pictures/pics/misc/cigar.jpg /home/sv452/Pictures/pics/misc/pearl_necklace.jpg /home/sv452/Pictures/pics/misc/see_no_evil.jpg /home/sv452/Pictures/pics/misc/cherry2.jpg /home/sv452/Pictures/pics/misc/phone.jpg /home/sv452/Pictures/pics/misc/shadow.jpg /home/sv452/Pictures/pics/misc/nipple.jpg /home/sv452/Pictures/pics/misc/collar.jpg /home/sv452/Pictures/pics/misc/feather.jpg /home/sv452/Pictures/pics/misc/piercing.jpg /home/sv452/Pictures/pics/misc/paint.jpg /home/sv452/Pictures/pics/misc/hug.jpg /home/sv452/Pictures/pics/misc/drop.jpg /home/sv452/Pictures/pics/misc/triples.jpg /home/sv452/Pictures/pics/misc/death.jpg /home/sv452/Pictures/pics/misc/ice.jpg /home/sv452/Pictures/pics/misc/rose4.jpg /home/sv452/Pictures/pics/misc/train.jpg /home/sv452/Pictures/pics/misc/whiff.jpg /home/sv452/Pictures/pics/misc/*****.jpg /home/sv452/Pictures/pics/misc/optica.jpg /home/sv452/Pictures/pics/misc/bunny.jpg /home/sv452/Pictures/pics/misc/zebra.jpg /home/sv452/Pictures/pics/misc/wc.jpg /home/sv452/Pictures/pics/misc/mirror.jpg /home/sv452/Pictures/pics/misc/ass3.jpg /home/sv452/Pictures/pics/misc/120cm.jpg /home/sv452/Pictures/pics/misc/river.jpg /home/sv452/Pictures/pics/misc/private.jpg /home/sv452/Pictures/pics/misc/road.jpg /home/sv452/Pictures/pics/misc/rose3.jpg /home/sv452/Pictures/pics/misc/jeans.jpg and on and on and on .......



any ideas why it fails with *arithmetic expression: syntax error: " /180 "* ??

---

### Post by hartz on 2007-11-05
Do you actually have a file with ***** (asterixes) in the file name or did you blank something out?

If you do have a file with *s in the name, please remove the file and try again.

Otherwise, please change the first line of the script to read

#!/bin/bash

No spaces, and it must be the very first line, no open lines above it :-)

---

