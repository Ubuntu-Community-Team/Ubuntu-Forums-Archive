---
title: "Converting video from one format to another"
date: 2005-08-31
forum: General Help
---

### Post by MeneM on 2005-08-31
Hello all,

I create video's from my kid, but the video's are quite large and it simple makes sense to encode them into something a little smaller. Like Ogg video or Xvid.

The video's out of the camera are avi files. What type of Avi is unknown to me...

I looked at some programs but most of the program's or howto's are commandline based. I'm looking for a nice GUI type program. Do you know irfanview? Well Irfanview can convert from one type of picture into another, png -> jpg, gif -> bmp that sort of thing.

Where can I find a irfanview sort of app for video files? (Something that can also run in Ubuntu ofcourse  ;-)  )

Thanks,
MeneM

---

### Post by arnieboy on 2005-08-31
[QUOTE=MeneM]Hello all,

I create video's from my kid, but the video's are quite large and it simple makes sense to encode them into something a little smaller. Like Ogg video or Xvid.

The video's out of the camera are avi files. What type of Avi is unknown to me...

I looked at some programs but most of the program's or howto's are commandline based. I'm looking for a nice GUI type program. Do you know irfanview? Well Irfanview can convert from one type of picture into another, png -> jpg, gif -> bmp that sort of thing.

Where can I find a irfanview sort of app for video files? (Something that can also run in Ubuntu ofcourse  ;-)  )

Thanks,
MeneM[/QUOTE]

instead of using ten clicks to do it from a gui try these two one line commands:
```
sudo apt-get install ffmpeg
```

```
ffmpeg -i file.avi -y -f vcd -vcodec mpeg1video -map 0.0:0.0 -b 1150 -s 352x240 -r 29.97 -g 12 -qmin 3 -qmax 13 -hq -acodec mp2 -ab 224 -ar 44100 -ac 2 -map 0.1:0.1 movie.mpg
```
where u have to replace "file.avi" with the name of the input file and "movie.mpg" with the desired output file name.

make sure u are in the directory which has the input file when u issue the ffmpeg command or u have to put the whole path name.

---

### Post by MeneM on 2005-08-31
Hi,

Thanks for your answer, but I would have to learn all those commands. When anything goes wrong, or I want to use a different resolution/codec I will have to know the program.

With a gui these commands are done by the gui. I'd just select the input file, and choose what I want to do with it.

I can't believe that such a program does not exist?

Mark

---

### Post by arnieboy on 2005-08-31
[QUOTE=MeneM]Hi,

Thanks for your answer, but I would have to learn all those commands. When anything goes wrong, or I want to use a different resolution/codec I will have to know the program.

With a gui these commands are done by the gui. I'd just select the input file, and choose what I want to do with it.

I can't believe that such a program does not exist?

Mark[/QUOTE]
u dont have to learn any command by rote. just do a ```
man ffmpeg
``` and it will give u all possible options. try learning all possible options in a gui that fast.
ffmpeg does have a GUI frontend to it but its currently in its alpha version:
[http://sourceforge.net/projects/xmffmpeg/](http://sourceforge.net/projects/xmffmpeg/)
u may try it out.

---

### Post by MeneM on 2005-09-01
Hi,

As there are no ubuntu packages available for xmffmpeg (and I'd like to try and not install from source. Easier maintanance) I'm learning to use ffmpeg on the commandline.

You where right, it is not that difficult.

On more question then, can some tell me how to batch process multiple files into new ones?

mvi_xxx.avi -> xxx.avi

Where xxx is a number.

Thanks,
Mark

---

### Post by crmanski on 2005-09-06
avidemux works pretty well and provides a gui for video conversion/processing. 
```
apt-get avidemux

```
 I made a script that uses ffmpeg and gives you a limited gui to convert files from AVI/MOV/MPG to DVD, SVCD or VCD compliant videos.
(Script is here: [http://ubuntuforums.org/showthread.php?t=62625](http://ubuntuforums.org/showthread.php?t=62625) ) 
Hope this helps.

---

### Post by Zyphrexi on 2005-11-06
ffmpeg is scary, i wish there was a gui

---

### Post by troughton on 2005-12-04
thanks for the code have tried many programs to do this but this is only one to work so putting in a coment so i can find it again as found it on my frends pc the other day and have spent 2 weeks trying to find it again on my computer as same serch poramiters on both computers bring up diferent results for some reason

---

