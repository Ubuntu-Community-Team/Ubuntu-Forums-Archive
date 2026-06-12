---
title: "dvd-slideshow"
date: 2006-10-27
forum: General Help
---

### Post by bengtt on 2006-10-27
I am having some problems with dvd-slideshow in edgy.
It seems to hang on mpeg2enc.

I did the following:

create test78 (or whatever) directory
cd test78

Create the following slideshow.txt file
--------- CUT -----
debug=3
title:5:Created slideshow
./1.JPG:5
./2.JPG:5
fadeout:2
--------- CUT ------

Put two pictures in the same directory, called 1.JPG and 2.JPG

Give the following command, and observe the printout
   dvd-slideshow -n 'test complete' -f ./slideshow.txt

For me, it hangs here...
> ....
> [dvd-slideshow] Fadeout 0:0:2.0
> [dvd-slideshow]########################################
> [dvd-slideshow] end_frame_number=506 end_time=0:0:16.88
> <subpictures>
>         <stream>
> [dvd-slideshow] waiting for mpeg2enc to finish...


If I check the process...
bengt     5582  5221 30 18:52 pts/1    00:00:26 mpeg2enc -v 0 -q 4 -4 2 -2 1 -a 2 -M 3 -f 8 -o /home/bengt/slask/dvd-slideshow_temp_5221/video_0.mpg


Do any one have any tips?
I could not find anything to relevant with google...

---

### Post by bengtt on 2006-10-28
Found this link:
[http://ubuntuforums.org/showthread.php?t=211825&page=2&highlight=dvd-slideshow](http://ubuntuforums.org/showthread.php?t=211825&page=2&highlight=dvd-slideshow)

After installing 0.7.5 from the website, it worked fine

---

### Post by Keith_Beef on 2006-11-28
I'm having trouble with dvd-slideshow, too.

I have a set of JPEG files, I have my parameter file like this:
```
frame-00000.jpg:5:Niagara Falls
frame-00001.jpg:5
frame-00002.jpg:5
```

My command line looks like this:
```
dvd-slideshow -o ../Output_files/ \
-n "Niagara falls and Toronto, November 2006" \
-p -L -f parameters2.txt
```

```
[dvd-slideshow]            dvd-slideshow 0.7.2
[dvd-slideshow]            Licensed under the GNU GPL
[dvd-slideshow]            Copyright 2003-2005 by Scott Dylewski
[dvd-slideshow]
[dvd-slideshow] Parsing input .txt file parameters2.txt
[dvd-slideshow] ########################################
[dvd-slideshow] Found 15 images and 0 audio files.
[dvd-slideshow] Video: PAL  Audio: AC3
[dvd-slideshow] Debug=0  Autocrop=0 Subtitles=render
[dvd-slideshow] Total video length = 0:1:15.0
[dvd-slideshow] WARNING: Using low-quality mode.  Audio and chapter
[dvd-slideshow]   timings may be off.  This mode is for testing only.
[dvd-slideshow]   output resolution is 352x288
[dvd-slideshow]   Ignore the '++WARN: [mpeg2enc]' lines
[dvd-slideshow] Output filename is Niagara_falls_and_Toronto,_November_2006
[dvd-slideshow] Temporary directory is ../Output_files//dvd-slideshow_temp_1770
[dvd-slideshow] Creating black background
[dvd-slideshow]########################################
[dvd-slideshow] 1/15 frame-00000.jpg 0:0:5.0
[dvd-slideshow] Subtitle= Niagara Falls
[dvd-slideshow]########################################
subtitle=Niagara Falls
[dvd-slideshow] 2/15 frame-00001.jpg 0:0:5.0
[dvd-slideshow]########################################
subtitles different i= i-1=Niagara Falls
[dvd-slideshow] 3/15 frame-00002.jpg 0:0:5.0
[dvd-slideshow]########################################
[dvd-slideshow] 4/15 frame-00003.jpg 0:0:5.0
[dvd-slideshow]########################################
[dvd-slideshow] 5/15 frame-00004.jpg 0:0:5.0
[dvd-slideshow]########################################
[dvd-slideshow] 6/15 frame-00005.jpg 0:0:5.0
[dvd-slideshow]########################################
[dvd-slideshow] 7/15 frame-00006.jpg 0:0:5.0
[dvd-slideshow]########################################
[dvd-slideshow] 8/15 frame-00007.jpg 0:0:5.0
[dvd-slideshow]########################################
[dvd-slideshow] 9/15 frame-00008.jpg 0:0:5.0
[dvd-slideshow]########################################
[dvd-slideshow] 10/15 frame-00009.jpg 0:0:5.0
[dvd-slideshow]########################################
[dvd-slideshow] 11/15 frame-00010.jpg 0:0:5.0
[dvd-slideshow]########################################
[dvd-slideshow] 12/15 frame-00011.jpg 0:0:5.0
[dvd-slideshow]########################################
[dvd-slideshow] 13/15 frame-00012.jpg 0:0:5.0
[dvd-slideshow]########################################
[dvd-slideshow] 14/15 frame-00013.jpg 0:0:5.0
[dvd-slideshow]########################################
[dvd-slideshow] 15/15 frame-00014.jpg 0:0:5.0
[dvd-slideshow]########################################
<subpictures>
        <stream>
[dvd-slideshow] waiting for mpeg2enc to finish...
```

This hangs around forever, so I press CTRL-c.

```
[dvd-slideshow] cleanup...
```


When I look in the temporary subdirectory of the output directory, I find a lot of totally black PPM images and one red image with the caption "Niagara Falls".

It looks as if an intermediate step of converting JPEG to PPM (as when using jpeg2yuv (as described [here)]("http://www.stillhq.com/jpeg2mpeg/") is failing.

Any ideas?

Beef

---

### Post by jaimedavila on 2006-12-07
I had the same problem, getting a lot of completely dark ppm files, and mpeg2somethingsomething hanging. The problem was solved by applying the steps outlines in the link above (in a previous post). Namely, uninstall the version of dvd-slideshow that ubuntu got from the repositories, and install the .deb file from the program's download area.

---

