---
title: "recording my desktop - alternatives?"
date: 2007-10-31
forum: General Help
---

### Post by phillips321 on 2007-10-31
Hi guys,

I can already record my desktop using gtk-recordmydesktop and this has proved a very good tool.

My problem is that the videos i record i then want to upload to the web so people can view them.

gtk-recordmydesktop outputs the video as an *.ogg file.

I need to host the videos on the net for people to watch, googlevideos compresses the video down far too much and makes the text un-readable. What other recording options are available for myself? Could i possibly record in flash?

Cheers in advance

---

### Post by DarkStarAeon on 2007-11-03
I don't know of a better tool than gtk-recordmydesktop personally...

but....you can always convert the .ogg files to whatever format you want.

To convert .ogg to .flv you can use WinFF which is a very easy to use front-end to FFMPEG:
[http://biggmatt.com/winff/](http://biggmatt.com/winff/)

Download the .deb file and install it. Make sure you have ffmpeg and ffmpeg2theora installed first in Synaptic though.

or....

Personally, to convert .ogg to .flv I use FFMPEG in a terminal. It looks like a long process below, but once you do it one time you'll see it's not hard at all.

Open Synaptic and install ffmpeg and ffmpeg2theora

Put the .ogg file you want to convert on your Desktop.

Now open a terminal and type: cd /home/username/Desktop

(replace username with your username of course)

In the terminal type this in, but see the breakdown of the command below first:

ffmpeg -i inputfilename.ogg -b 128 -s 400x240 -pass 1 -passlogfile log-file outputfilename.flv

Breakdown of the command...

the -i is for input

change inputfilename.ogg to your files name

-b is the bit rate, set it to what you want it to be.

-s is the size you want the output file to be, change it to what you need.

change outputfilename.flv to what you want your flv file to be named.

There ya go. Now just copy and paste that command into a .txt file and save it so you can just modify it 
and paste it into a terminal later when you want to use it to convert more files.

p.s.

I use gtk-recordmydesktop, then to convert those .ogg files to .avi I use the package named iriverter, just search for iriverter in Synaptic and install it.

---

### Post by AgentZ86 on 2007-12-24
Hi thanks
I've used the WinFF, and seem to work, however the flash video seems a bit blurry.

when the conversion takes place. Is is suppose to be blurry slightly, or less quality ?

I basically don't really need it to be flash it can be any other web compatible video format like real player etc. 

how can I convert my ogg file to be played with the embed real player for only use etc.

Any ideas 
Thanks

---

### Post by Samhain13 on 2007-12-24
I go with DarkStarAeon's suggestion. That's how I make my videos too (those that I upload to YouTube, for example), as far as using FFMpeg and/or FFMpeg2Theora. MEncoder is also a great tool for transcoding OGG to other formats.

But if you can get a hold of a hosting service provider, you can also try something called [iTheora](http://menguy.aymeric.free.fr/theora/index.php?l=en). It's a PHP application that lets people watch/listen to streaming OGG files through a Java applet.

Cheers and happy Christmas! :)

---

### Post by DarkStarAeon on 2007-12-24
You could always convert it to AVI using this command:

**mencoder inputfilenamehere.ogg -o outputfilenamehere.avi -vf scale=400:240 -oac mp3lame -ovc lavc**

You can change the size where it says 400:240

Of course change the inputfilenamehere.ogg to the name of your ogg file. Change the outputfilenamehere.avi to what you want the .avi file to be named.

...or...

You can install a program called iriverter in your package manager, and use it to convert .ogg files to a few different mobile and/or lightweight formats.

...or....

You can manually convert the file to .avi with the command up above in this post, then use Mobile Media Converter to make it what format you want:

[http://www.miksoft.net/products/mmc-lin.tar.gz](http://www.miksoft.net/products/mmc-lin.tar.gz)

Download that file, extract it, and run it.

---

### Post by AgentZ86 on 2007-12-27
> **DarkStarAeon said:**
> You could always convert it to AVI using this command:

**mencoder inputfilenamehere.ogg -o outputfilenamehere.avi -vf scale=400:240 -oac mp3lame -ovc lavc**

You can change the size where it says 400:240

Of course change the inputfilenamehere.ogg to the name of your ogg file. Change the outputfilenamehere.avi to what you want the .avi file to be named.

...or...

You can install a program called iriverter in your package manager, and use it to convert .ogg files to a few different mobile and/or lightweight formats.

...or....

You can manually convert the file to .avi with the command up above in this post, then use Mobile Media Converter to make it what format you want:

[http://www.miksoft.net/products/mmc-lin.tar.gz](http://www.miksoft.net/products/mmc-lin.tar.gz)

Download that file, extract it, and run it.

Yep, I've tried the iriverter also works nice, 

Those who like the clickety way Seriously the WinFF is a nice way to go converts to just about anything.
I'm not sure how to increase the quality or perhaps just some setting I need to change when I recorded to begin with but the interface is super simple.

It uses the mencoder and the FFmpeg thing everyone suggests also.

[http://biggmatt.com/files/winff.032-i386.deb](http://biggmatt.com/files/winff.032-i386.deb)

Just click and it will install it from here using your dep. package installer on ubuntu. You don't really have to do anything else.

This is some dudes site name [www.BigMatt.com](www.BigMatt.com)
Pretty cool really.

FYI i'm using Gutsy with all the latest updates so not sure if that will effect how it may run for you, but it does work pretty nice from what I've done so far.

I've converted OGG to flv and OGG to WMV and things like that there is a pulldown menu for selecting your output file type you want to convert to.

Well hope this helps happy hacking.
:popcorn:

---

### Post by Irony on 2007-12-27
Vidcap works great, its easy to install and will make youtube comopatible videos;

[http://sourceforge.net/project/showfiles.php?group_id=81535](http://sourceforge.net/project/showfiles.php?group_id=81535)

---

