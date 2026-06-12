---
title: "Too big an MPEG file for DVD"
date: 2005-10-12
forum: General Help
---

### Post by cazz on 2005-10-12
I recording some MPEG file but some is very big as 4.6 GB MPEG file.
I dont want to split the file but I like to change the quality so I can create av DVD disc to play on my DVD player.

Is that any program that I can change how much the outputfile going to be and the program do the rest?

---

### Post by glug101 on 2005-10-12
[QUOTE=cazz]I recording some MPEG file but some is very big as 4.6 GB MPEG file.
I dont want to split the file but I like to change the quality so I can create av DVD disc to play on my DVD player.

Is that any program that I can change how much the outputfile going to be and the program do the rest?[/QUOTE]
My understanding is that a 4.6 gig file would fit on a dvd, but I'm sure you have your own reasons for splitting it :)  Mencoder is a program that comes packaged with mplayer (available through Synaptec).  It can do a copy of the file and split it into chunks that are smaller without changing the quality of the video.

mencoder -of mpeg -ss HH:MM:SS -endpos HH:MM:SS -oac copy -ovc copy <name of input file> -o <name of output file>.mpg

-ss start encoding at point HH:MM:SS
-endpos stop encoding at point HH:MM:SS
-of ouput container format (in this case mpeg)
-oac output audio codec
-ovc output video codec
-o ouput file name

---

### Post by cazz on 2005-10-12
hmm I dont like to split the mpeg file. :) 
I want to change the quality so the MPEG file is not too big.
I going to use dvdauthor after that.

---

### Post by glug101 on 2005-10-12
[QUOTE=cazz]hmm I dont like to split the mpeg file. :) 
I want to change the quality so the MPEG file is not too big.
I going to use dvdauthor after that.[/QUOTE]
Well, if you don't mind loosing quality, you can transcode it through ffmpeg.

*ffmpeg -hq -target svcd <input file name> -o <output file name>.mpg*

Keep in mind that you may have to change svcd to a specific format (use either ntsc-svcd or pal-svcd depending on your location or needs).  There are also other options for the target that I am less familiar with. (Google for it, I know they're there).

Maybe use ffmpeg to transcode the file into an avi divx file or similar to decrease file size and keep more of the quality than svcd.  The beauty of svcd is, however, that it works in many dvd players like that and you can get a LOT more on a dvd.  However, the quality is just a little better than VHS, not dvd quality at all.

The option that I would use (so as not to loose quality) would be to do the mencoder trick to break it up for transport (if that is what you are doing) and then connect the pieces on the other end.  But, do what you want.  That's the beauty of Linux ;)

Hope this helps!

---

### Post by cazz on 2005-10-12
Thanks I have think about it sometime.

But SVCD is on a 700 MB CD disc?
I have try to use DVD instead but then is MPEG file still too big :D

---

### Post by Hairy_Palms on 2005-10-12
what do you mean the file is too big? a DVD can hold 4.7GB for a single-side single layer disc.

---

### Post by cazz on 2005-10-12
what I understand a 4.7 GB DVD disc only can burn 4482.63 MB

---

### Post by glug101 on 2005-10-12
[QUOTE=cazz]Thanks I have think about it sometime.

But SVCD is on a 700 MB CD disc?
I have try to use DVD instead but then is MPEG file still too big :D[/QUOTE]
Ok, I think I understand now.  You have a file that is too large to fit on a single dvd and so you would like to tweak the compression just a little bit so that it will fit on a dvd, but still play back on a standard dvd player?

I'm not sure this is possible, but I don't have any experience with dvd authoring.  Using ffmpeg you could adjust the video bit rate  (using the -b option) to change the video bit rate to a lower value to increase the compression.  The possible downside to this is that you might end up with a DVD that is out of spec, and will not work in a standard dvd player.  Perhaps somebody else with more experience would know what bit rates are valid for a standard dvd....

---

### Post by cazz on 2005-10-12
[QUOTE=glug101]Ok, I think I understand now.  You have a file that is too large to fit on a single dvd and so you would like to tweak the compression just a little bit so that it will fit on a dvd, but still play back on a standard dvd player?

I'm not sure this is possible, but I don't have any experience with dvd authoring.  Using ffmpeg you could adjust the video bit rate  (using the -b option) to change the video bit rate to a lower value to increase the compression.  The possible downside to this is that you might end up with a DVD that is out of spec, and will not work in a standard dvd player.  Perhaps somebody else with more experience would know what bit rates are valid for a standard dvd....[/QUOTE]

Yes
Sorry is hard sometime to explain sometime :) :rolleyes:

---

### Post by glug101 on 2005-10-12
[QUOTE=cazz]Yes
Sorry is hard sometime to explain sometime :) :rolleyes:[/QUOTE]
English is hard even if your native country speaks it ;)

I did a little more digging, and I think that the dvd spec DOES support different bit rates.  You might want to find one of the many bitrate calculators to decide on a bitrate, but assuming that your current file has a video bitrate at the standard 3.1 Mb/s, I would imagine that a 2 Mb/s or similar video bitrate would work for you.  

Good luck! (with the computer and english ;) )

---

### Post by damir on 2005-10-13
Avidemux2

Compile it from source (you must have ffmpeg and/or lavc installed) and install.
Best proggy for video encoding/recoding/...

---

