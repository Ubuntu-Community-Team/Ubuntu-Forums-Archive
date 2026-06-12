---
title: "Subtitles on Totem"
date: 2005-04-01
forum: General Help
---

### Post by Gusman on 2005-04-01
Trying to load movies with subtitles on totem has been a frustrating task for me in the past few days.
After searchig extensively the forums and the internet after an answer that would solve this problem, I had to give up and post this asking you guys for help.

I'm using totem-xine.

I've already tryed giving the same filename for both the movie and the subtitle (e.g. file.avi, file.srt). I've also tryed both sub and srt subtitle format. Totem loaded the movie fine but ignored any subtitle. Of course I had both the movie and the subtitle on the same folder.

I've tryed loading them manually via terminal (totem file:///file.avi#subtitle:file.srt). In this case totem opens but returns an error message: "Totem could not play 'file:///file.avi#subtitle:file.srt" - The specified movie could not be found.
If I type the following command - totem file:///file.avi - totem opens with no error messages but with no movie loaded.

I'm sure I am forgetting something but just can't figure out what it is. I tryed also gxine, and it loaded subtitles normally.

Thank's in advance for your help
Gusman

---

### Post by bored2k on 2005-04-01
I suggest you install vlc. With it you can manually load subtitles with the movies. Totem is a pain @ times recognizing subtitles [gxine also]. So give vlc a try, you'll like it ;) [you might want to get debian files from videolan.org, the new vlc is rockin'].

---

### Post by Gusman on 2005-04-01
Thanks for the tip.
I was hoping to stick with programs that are Ubuntu's default, but I'll sure will give VLC a try.
Anyway it's good to know I'm not the only one with problems :)

Gusman

---

### Post by moon2js on 2005-04-24
I've run into a similar problem. I was checking to see subtitle support under totem-xine because I'm much rather stick to totem than mess with others.

And "srt" subtitles worked automatically. And they are much nicer looker than under the mplayer I was using in Warty. I was so surprised because this was always such an hassle in my Warty/mplayer setup.

But I can't seem to get "sub" subtitles files to work at all. Is this a lacking in the program or do I have the syntax wrong?

if the movie file and subtitle is called "moment," then I try:
```
totem moment.avi#subtitle:moment.avi
```
and it doesn't work. I found that syntax online, but maybe I misinterpreted it?

On the other hand,```
totem moment.avi
```
works fine, playing the video file fine, but without subtitles.

---

### Post by kjempe on 2006-01-11
[QUOTE=moon2js]"srt" subtitles worked automatically. And they are much nicer looker than under the mplayer I was using in Warty. I was so surprised because this was always such an hassle in my Warty/mplayer setup.[/QUOTE]

if you do run either wine or a seperate windows os, you could try the following to convert your .sub-file to a .srt-file:

1- install the newest version of subrip.
2- rename .sub to .vob
3- open up subrip and select 'file/open vob'
4- click on 'open dir' on the right then select the new .vob file
5- check the square next to the .vob file
6- push start
7- push ok
8- type in the matching characters in the red box. you only need to do it a couple of times before it autodetects all the characters.
9- now, that you have the .srt-file, rename it to match the .avi-file so when you open up the .avi-file in a player it will load the subtitles automatically

i found those instructions somewhere on the internet and didn´t try it out yet. but i sure will though i got the same problem playing subtitles in totem.

---

### Post by CompShrink on 2006-02-04
Or if you want to stay purely linux...

Try this perl script:
[http://www.robelix.com/sub2srt/](http://www.robelix.com/sub2srt/)

I've used a program called simply "subs" to convert .sub to .srt... but I don't have that anymore, and it's not an easy program name to Google on, you know? Try that perl script though, if you're still looking here.

---

### Post by AncientPC on 2007-05-14
> **moon2js said:**
> if the movie file and subtitle is called "moment," then I try:
```
totem moment.avi#subtitle:moment.avi
```
and it doesn't work. I found that syntax online, but maybe I misinterpreted it?

It should be subtitle:moment.srt, but even correcting for that error still gives me a problem.

---

### Post by Angelbeast on 2007-05-20
I have quite a few movies with subtitles. mostly Japanese. All of the subs in srt format work just fine in Totem. But yesterday i downloaded Lola Rennt with subs in srt format and it just won't work.  I checked again and the rest till work fine. Weird.

---

### Post by unluckyluke on 2007-07-04
> **CompShrink said:**
> Or if you want to stay purely linux...

Try this perl script:
[http://www.robelix.com/sub2srt/](http://www.robelix.com/sub2srt/)

I've used a program called simply "subs" to convert .sub to .srt... but I don't have that anymore, and it's not an easy program name to Google on, you know? Try that perl script though, if you're still looking here.
Sorry about the interruption, I am new in this forum, but the program you are probably talking about can be found in apt, simply writing this command:
sudo apt-get install libsubtitles-perl
.

Hope this helps!

---

### Post by adityakavoor on 2008-03-04
> **unluckyluke said:**
> Sorry about the interruption, I am new in this forum, but the program you are probably talking about can be found in apt, simply writing this command:
sudo apt-get install libsubtitles-perl
.

Hope this helps!

gr8 :)

---

### Post by uarale on 2008-07-04
For the subtitle to show, you need to go to Edit > Preferences, then choose "Automatically load subtitle files when movie is loaded".

I don't know why, but movies don't play when we type the command: totem file.avi#subtitle:file.srt

---

### Post by rastilin on 2008-07-14
It works, Totem loads .sub files perfectly once the option to do it automatically is set in the preferences. A bit anticlimatic actually.

---

### Post by Salomonis on 2008-07-24
Not for me.  I've tried to get .sub files to work for totem with no luck.  I don't want to have to convert them to .srt.  In my opinion it's simply "putting a band aid" on the problem.  In reality it's better not to cut yourself.  Evidence of bad programming.  What if you had to convert all video formats into .mpeg and you had to use a different program for each conversion.  Is it too much to ask for a program that plays all media formats and requires no conversions?  I can't even get subtitles to work with VLC.  It worked before the update,  maybe I'll have to restart.    I'll let yall know if that worked.

---

### Post by Salomonis on 2008-07-24
the subtitles option use to be under video tab in VLC, now it's gone.  I wish restarting was the answer, but of course life's not that simple.

---

### Post by Salomonis on 2008-07-24
Don't understand how but I got it to work by creating 2 .sub files

---

