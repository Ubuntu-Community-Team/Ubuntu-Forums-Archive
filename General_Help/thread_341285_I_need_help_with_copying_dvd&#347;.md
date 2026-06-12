---
title: "I need help with copying dvd&#347;"
date: 2007-01-18
forum: General Help
---

### Post by joriad on 2007-01-18
I have been having a problem copying dvd&#347; using xdvdshrink 2.6.1. The dvd copied to th dvd +r disc.  However, the video and audio are out of sync (video ahead of audio by about a second, annoying) and the disc would only play on my dvd drive but not my dvd player or playstation2 (disc not recognized). Does anyone have any suggestions as to  how to correct this, or maybe different programs to use instead of xdvdshrink? I am not very familiar with linux as of yet so step by step instructions would be very necessary. I want to copy the entire dvd including menus and extras so that it would function just as the original. 

Thanks

---

### Post by edward4130 on 2007-01-18
Not sure about what you are using, I stumbled a bit starting to do this and I found this to work great.  Thanks to my bro-in-law for gettign me started in the right direction with mplayer, it is in the third part multiverse, you need it to start.  I tried acidrip also in the multiverse as a front end to mplayer but I was not happy with the time expense, so I went to this.......

(I posted this before here is a repost)

As far as ripping DVD's, I have two commands/scripts that may help.  Both are
based upon mencoder, which comes as part of Mplayer.

The Mplayer guys are the Hungarian prodigies that bring all media to Unix.
And have available for download all of the Windows and Real player and Apple
codecs.    They have some wonderful documentation  that you could spend 2007
reading.

Put a DVD in, and try playing it from the command line with

mplayer dvd://1

And be sure that the "1" title is the one that you want.  Sometimes it is not.
Might be dvd://2, or dvd:3.   but usually it is 1.

Once you are sure it is 1, or whatever, run this in a directory with lots of
room:

mplayer -vo xv dvd://1 -dumpstream -dumpfile outfile.mpg


That command makes a large file called "outfile.mpg".   It basically just
plays the DVD, and dumps the mpg data that it reads,  The resulting file is
called "outfile.mpg", though you could call it whatever you want, or rename
it.  It will have video and audio.

If you want to compress it, there are loits of ways, I picked this script up
in the Knoppmyth forums.  Just paste into a file, and save as "rip.sh" or
something, and chmod +x.  Note, because it is in e-mail, you may have some
trouble with the whitespace on these and may need to do some testing on the
command line to get it right before pasting into a script.

From [http://mysettopbox.tv/phpBB2/viewtopic.php?t=12899](http://mysettopbox.tv/phpBB2/viewtopic.php?t=12899)

#!/bin/bash
THEFILE=$1
NEWFILE=`echo $THEFILE|sed 's/mpg/avi/'`
unlink frameno.avi 2> /dev/null
nice -n 19 mencoder $THEFILE -oac mp3lame -lameopts abr:br=128  -ovc
lavc -lavcopts vcodec=mpeg4:vhq:v4mv:vqmin=2:vbitrate=920:vpass=1 -ofps
25 -vf pp=de,scale=720:405 -o "/dev/null"
nice -n 19 mencoder $THEFILE -oac mp3lame -lameopts abr:br=128  -ovc
lavc -lavcopts vcodec=mpeg4:vhq:v4mv:vqmin=2:vbitrate=920:vpass=2 -ofps
25 -vf pp=de,scale=720:405 -o $NEWFILE unlink divx2pass.log  2> /dev/null

Actually, on the Mplayer documentation pages, I picked up an example that
works faster for me:

#!/bin/bash
mencoder dvd://1 -ovc lavc -lavcopts vcodec=mpeg4:vpass=1 -oac
mp3lame -lameopts vbr=3 -o /dev/null
mencoder dvd://1 -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell:vpass=2 -oac
mp3lame -lameopts vbr=3 -o output.avi

rm -f divx2pass.log

These do take a long time, longer than the movie took, but they are also
encoding it.  The quality is coming out great for me, better than cable tv
quality, not as good as DVD or HD of course.  The straight rip command takes
about half as long as the play time, I think, never timed it I always stepped away.

Here is the documentation page:
[http://www.mplayerhq.hu/DOCS/HTML/en/index.html](http://www.mplayerhq.hu/DOCS/HTML/en/index.html)

---

### Post by flossgeek on 2007-01-18
DVD::rip - [http://www.exit1.org/dvdrip/](http://www.exit1.org/dvdrip/)

It is available in the repositorys.

---

### Post by gwpritch on 2007-01-18
I use the original windows dvdshrink under wine.  Works really well and has a nice gui from which you can look at the dvd contents, compress whole disk or re-author as you choose.
K9copy also is very user friendly although I have had some issues with it not being able to open some disks.
As to video and audio being out of sync...I have noticed this problem with different players.  They can be totally in sync playing with totem-xine but out of sync in mplayer or vlc. Mplayer gives you the option of applying a delay to resync if necessary.
When burning to DVD are you burning the entire video_ts folder or just its contents. If the data is not inside the folder, the standard dvd player will not play the disk even though you may be able to play it on the computer.

---

### Post by m1215 on 2007-01-18
i followed these two links [http://forum.digital-digest.com/showthread.php?t=74727](http://forum.digital-digest.com/showthread.php?t=74727) [http://mysite.verizon.net/vzer15pr/wildchildscustomcomputers2/id17.html](http://mysite.verizon.net/vzer15pr/wildchildscustomcomputers2/id17.html)
worked great. i used to dual boot  xp because it was the only way to backup the kids movies. once working with wine, there was no reason to keep xp around.

---

### Post by orb9220 on 2007-01-18
yep dvdshrink under wine works great. 
[https://help.ubuntu.com/community/DVDShrink](https://help.ubuntu.com/community/DVDShrink)
[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)

---

### Post by joriad on 2007-01-20
Thanks for your help in trying to solve this problem. I have tried dvdshrink and decrypter but still I have had no luck. I still can play the video on the computer but as for my dvd players I get one that doesn't recognize that there is even a dvd in the player, the other one recognizes there is a dvd and starts to play but i get no audio or video, I can even fast forward the and run through chapters and the timer even tells me its playing the movie but still no audio or video, only the dvd default blue screen appears. If anyone has any advice that would be great. Maybe there is a setting that is not correct or maybe i am saving as the wrong type (.iso), hopefully it is something simple like that. I am using dvd +r, which is what one dvd player accepts. maybe using a dvd -r would work. at this point I am very confused. 

thanks for all your help

---

### Post by nix4me on 2007-01-20
k9copy

nix4me

---

### Post by joriad on 2007-01-27
Thanks for all the help everyone, I got everything working with K9copy and k3b. I am still unsure as  to why dvdshrink and decypher would not work with my system, but as long as I have one set that will is ok by me. Thanks again for all your help.

---

