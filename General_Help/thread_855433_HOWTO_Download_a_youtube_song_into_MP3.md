---
title: "HOWTO: Download a youtube song into MP3"
date: 2008-07-10
forum: General Help
---

### Post by ForksHolder on 2008-07-10
Hello!

Well, This is something that helps me very much and i wanted to share it with you.

In this small HOWTO i'm going to explain how to download song from youtube to MP3 format.

For example, Here is the song "Master Of Puppets" by "Metallica":
> [http://www.youtube.com/watch?v=_z-hEyVQDRA](http://www.youtube.com/watch?v=_z-hEyVQDRA)

I'll teach you how to download the SONG master of puppets.

SO LET'S BEGIN!

**Installation**
First, We're going to install 2 simple software from Ubuntu repos.

Open Terminal (Applications -> Accessories -> Terminal), and type:
> sudo apt-get install ffmpeg youtube-dl

Then enter your password (if needed) and type "Y" for anything he asks.


**Downloading a video to FLV format**
Now, In the terminal, Write the youtube-dl and the url to the movie you want to download. If you want to download the Master of puppets, enter this:

> youtube-dl [http://www.youtube.com/watch?v=_z-hEyVQDRA](http://www.youtube.com/watch?v=_z-hEyVQDRA)

Now it should download it to FLV format. (This may take about a miniute to download)

**Turning the FLV to a normal MP3 song**

now, to see what is the FLV's name, enter this command:
> ls *flv
For the Master Of Puppets, it should be this name:
> holder@holder-laptop:~$ ls *flv
_z-hEyVQDRA.flv


Copy the name of it, and make this command for MP3 turning:
> ffmpeg -i _z-hEyVQDRA.flv MasterOfPuppets.mp3
(Again, This should take some time.)

To check if it covert it successfully, make this command:
> ls *mp3
and if you did all right, you should see the "MasterOfPuppets.mp3" in the list.


**Cleanning**
When you got the mp3 file, you don't need the FLV anymore, so delete by this command:

> rm _z-hEyVQDRA.flv




That's it! now you have the mp3 song saved in your computer :]

Enjoy,
~Forks Holder.

---

### Post by fedex1993 on 2008-07-11
yes this might be better to post in the tutorials sections of the forums since this is actually general help forum. Still pretty cool thoe

---

### Post by ForksHolder on 2008-07-11
> **fedex1993 said:**
> yes this might be better to post in the tutorials sections of the forums since this is actually general help forum. Still pretty cool thoe


Bah sorry =/

If there is an administrator here, please move it. :)

---

### Post by chris4585 on 2008-07-11
**_You need youtube-dl and ffmpeg for this to work right_**

After seeing this guide/tutorial I know this was my chance to learn bash, well it took me about 2 hours? of learning, and testing, and its not perfect, but it works nicely.

Step 1

Paste that into gedit or nano or whatever your favorite editor is, save it as. yt2mp3

```
#!/bin/bash
echo Enter the youtube url to begin downloading the video.
read VIDEO
echo What is the artist of the song?
read ARTIST
echo What is the name of the song?
read NAME
youtube-dl $VIDEO -o "${ARTIST} - ${NAME}.flv"
ffmpeg -i "${ARTIST} - ${NAME}.flv" "${ARTIST} - ${NAME}.mp3"
rm -rf "${ARTIST} - ${NAME}.flv"
echo Your video is finally converted into a mp3!
```

Step 2

then run
```

chmod +x yt2mp3

sudo mv yt2mp3 /bin/
```

Now you can run yt2mp3 and download your video and convert it in no time :)

feed back, please, since this is my first bash script pretty much.

Nice guide btw

---

### Post by ForksHolder on 2008-07-13
> **chris4585 said:**
> **_You need youtube-dl and ffmpeg for this to work right_**

After seeing this guide/tutorial I know this was my chance to learn bash, well it took me about 2 hours? of learning, and testing, and its not perfect, but it works nicely.

Step 1

Paste that into gedit or nano or whatever your favorite editor is, save it as. yt2mp3

```
#!/bin/bash
echo Enter the youtube url to begin downloading the video.
read VIDEO
echo What is the artist of the song?
read ARTIST
echo What is the name of the song?
read NAME
youtube-dl $VIDEO -o "${ARTIST} - ${NAME}.flv"
ffmpeg -i "${ARTIST} - ${NAME}.flv" "${ARTIST} - ${NAME}.mp3"
rm -rf "${ARTIST} - ${NAME}.flv"
echo Your video is finally converted into a mp3!
```

Step 2

then run
```

chmod +x yt2mp3

sudo mv yt2mp3 /bin/
```

Now you can run yt2mp3 and download your video and convert it in no time :)

feed back, please, since this is my first bash script pretty much.

Nice guide btw


First of all, It's nice that you leaned such things, it will help you if in the future you'll want to program something.

Anyways,
You can download and convert it by your way, but editing the file will be kinda long when you can just make it by 1 command.. but very nice idea (: keep thinking of doing Howto's, it's helping a lot the Ubuntu community.

Thanks,
~ForksHolder.

---

### Post by AnLGP on 2008-07-13
Um.  I might be out of line but:

Is this something that should be promoted here?

---

### Post by ForksHolder on 2008-07-13
> **AnLGP said:**
> Um.  I might be out of line but:

Is this something that should be promoted here?

As i was writing,
It's a HOWTO, not General help. I have missed click.

Anyway, If there is a moderator here, please move it.

---

### Post by AnLGP on 2008-07-13
I'm not speaking on where it should be but to the morality of the howto

---

### Post by faze3 on 2009-05-03
> **ForksHolder said:**
> Hello!

Well, This is something that helps me very much and i wanted to share it with you.

In this small HOWTO i'm going to explain how to download song from youtube to MP3 format.

For example, Here is the song "Master Of Puppets" by "Metallica":


I'll teach you how to download the SONG master of puppets.

SO LET'S BEGIN!

**Installation**
First, We're going to install 2 simple software from Ubuntu repos.

Open Terminal (Applications -> Accessories -> Terminal), and type:


Then enter your password (if needed) and type "Y" for anything he asks.


**Downloading a video to FLV format**
Now, In the terminal, Write the youtube-dl and the url to the movie you want to download. If you want to download the Master of puppets, enter this:



Now it should download it to FLV format. (This may take about a miniute to download)

**Turning the FLV to a normal MP3 song**

now, to see what is the FLV's name, enter this command:

For the Master Of Puppets, it should be this name:


Copy the name of it, and make this command for MP3 turning:

(Again, This should take some time.)

To check if it covert it successfully, make this command:

and if you did all right, you should see the "MasterOfPuppets.mp3" in the list.


**Cleanning**
When you got the mp3 file, you don't need the FLV anymore, so delete by this command:






That's it! now you have the mp3 song saved in your computer :]

Enjoy,
~Forks Holder.


Ok so i managed to download the youtube video successfully but when i tried to convert it to .mp3 it just made a file with 0 bytes (like an empty file)

on terminal the last line says "Unsupported codec for output stream #0.0"

can anyone help??

---

### Post by mb_webguy on 2009-05-03
There are actually multiple ways to do this.  If you want to do it completely using GUI applications, you can use the Video DownloadHelper extension (or similar extension) in Firefox to download the video, then VLC to strip the audio.  

Or, since the Video DownloadHelper extension has a conversion feature that allows you to specify the method(s) of conversion, you can use the ffmpeg method in the original post to allow you to download and convert the video to an mp3 in one step.

---

### Post by ckop64 on 2009-11-12
**Alternative Solution**: You might install and run Youtube Downloader in WINE. After that you can use the method to convert as described above.

---

### Post by wydesenej on 2010-01-27
Online convertor :KS

[http://www.video2mp3.net/](http://www.video2mp3.net/)

---

### Post by SuperSonic4 on 2010-01-27
First things first -- your song choice is made of WIN. \m/


Yeah, you're better off detailing howto download a generic flash video to mp3.

Personally I use [get-flash-videos]("http://code.google.com/p/get-flash-videos/") as it works on more than one site and being a terminal app you can cd to the directory you want beforehand.


Instead of ```
ffmpeg -i _z-hEyVQDRA.flv MasterOfPuppets.mp3 
```

may I suggest ```

ffmpeg -i _z-hEyVQDRA.flv -ac 2 -ab 128k MasterOfPuppets.mp3 
```

adding those two audio options will ensure that the file is in stereo and at 128kbps

---

### Post by azika on 2010-02-03
_[COLOR=dimgray]you can use voydo.com/convert to convert [/COLOR]_[[COLOR=dimgray]youtube to mp3[/COLOR]]("http://www.voydo.com/convert/")

---

### Post by azika on 2010-02-03
good trick thanks
> **ForksHolder said:**
> Hello!
 
Well, This is something that helps me very much and i wanted to share it with you.
 
In this small HOWTO i'm going to explain how to download song from youtube to MP3 format.
 
For example, Here is the song "Master Of Puppets" by "Metallica":
 
 
I'll teach you how to download the SONG master of puppets.
 
SO LET'S BEGIN!
 
**Installation**
First, We're going to install 2 simple software from Ubuntu repos.
 
Open Terminal (Applications -> Accessories -> Terminal), and type:
 
 
Then enter your password (if needed) and type "Y" for anything he asks.
 
 
**Downloading a video to FLV format**
Now, In the terminal, Write the youtube-dl and the url to the movie you want to download. If you want to download the Master of puppets, enter this:
 
 
 
Now it should download it to FLV format. (This may take about a miniute to download)
 
**Turning the FLV to a normal MP3 song**
 
now, to see what is the FLV's name, enter this command:
 
For the Master Of Puppets, it should be this name:
 
 
Copy the name of it, and make this command for MP3 turning:
 
(Again, This should take some time.)
 
To check if it covert it successfully, make this command:
 
and if you did all right, you should see the "MasterOfPuppets.mp3" in the list.
 
 
**Cleanning**
When you got the mp3 file, you don't need the FLV anymore, so delete by this command:
 
 
 
 
 
 
That's it! now you have the mp3 song saved in your computer :]
 
Enjoy,
~Forks Holder.
 
> **SuperSonic4 said:**
> First things first -- your song choice is made of WIN. \m/
 
 
Yeah, you're better off detailing howto download a generic flash video to mp3.
 
Personally I use [get-flash-videos]("http://code.google.com/p/get-flash-videos/") as it works on more than one site and being a terminal app you can cd to the directory you want beforehand.
 
 
Instead of ```
ffmpeg -i _z-hEyVQDRA.flv MasterOfPuppets.mp3 
```
 
may I suggest ```

ffmpeg -i _z-hEyVQDRA.flv -ac 2 -ab 128k MasterOfPuppets.mp3 
```
 
adding those two audio options will ensure that the file is in stereo and at 128kbps

---

### Post by Vaphell on 2010-02-03
Dumping audio data to file without any conversion is imho the best choice, additional conversions do nothing meaningful.

what if audio in flv is 64kbps mono? converting it to 128kbit stereo won't increase quality, and if the flv file is of much higher bitrate, you'd lose quality by compressing the audio.

---

### Post by muckblit on 2010-03-06
Thank you so much. I had tried Sound Recorder and got nothing. There was nothing muted. I tried different Input settings. Sound Recorder uses gnome-sound-recorder. I'm using ubuntu lucid in Feb 2010.

Your method is so easy. I use it like:

yt2mp3 [url]

or it waits for the url to be typed. More cute bashisms for you:

#!/bin/bash

video=${1:-$( read video )} # if you see a smiley face that's a colon then dash
echo What is the artist of the song?
read artist
echo What is the name of the song?
read name
if [ -n "$video" ] && [ -n "$artist" ] && [ -n "$name" ]
 then pushd ~/Music > /dev/null
 youtube-dl $video -o "${artist}_${name}.flv"
 ffmpeg -i "${artist}_${name}.flv" "${artist}_${name}.mp3"
 rm -rf "${artist}_${name}.flv"
 echo Your video is finally converted into a mp3!
 popd > /dev/null
else
 echo What is missing\? video\=$video artist\=$artist name\=$name
fi

---

### Post by shootersf on 2010-03-17
> **faze3 said:**
> Ok so i managed to download the youtube video successfully but when i tried to convert it to .mp3 it just made a file with 0 bytes (like an empty file)

on terminal the last line says "Unsupported codec for output stream #0.0"

can anyone help??
I had the same problem and found an answer here
[http://ubuntuforums.org/showpost.php?p=8370224&postcount=5](http://ubuntuforums.org/showpost.php?p=8370224&postcount=5)

---

### Post by scouser73 on 2010-03-17
You could always use this website to convert youtube videos to mp3: [http://www.video2mp3.net/](http://www.video2mp3.net/)

---

### Post by uRock on 2010-03-17
I just boot Windows and use RealPlayer to record. Much easier.

---

### Post by conradin on 2010-03-17
You know, there are firefox add ons that convert youtube vids to mp3.

---

### Post by jsuydam5 on 2010-04-13
[http://dirpy.com/](http://dirpy.com/) ...  You don't need any software or any commands! This is by far the best online Youtube to mp3 converter. It converts the video and downloads it at the same time for faster downloads than any other online ones. Another great thing about this site is instead of having to copy the url, you can search for the video right on dirpy so you can watch it, download the video file, or download the mp3. (although you can still copy and paste the url if you want) Also, you can edit the mp3 details directly online! (title, artist, album, year, genre...) You can also cut the length of the mp3 online as well! Heres the WOT Scorecard to prove its legit: [http://www.mywot.com/en/scorecard/dirpy.com](http://www.mywot.com/en/scorecard/dirpy.com)

---

### Post by samthjj67 on 2010-04-14
Try the freeware StreamTransport,  it works great for me.

---

### Post by lisati on 2010-04-14
Thread closed for review. See [here]("http://ubuntuforums.org/showthread.php?t=1429211")

---

