---
title: "wma to ogg converter"
date: 2006-11-23
forum: General Help
---

### Post by Dr Small on 2006-11-23
Hello.
I have been search Google for the past hour, trying to find some program to convert wma's to ogg.
But I can not find anything that is helpful, and most everything I download, I can't figure out how to 'install' it (me is a linux noob)

So, any suggestions for a simple program that does what I'm looking for, would be really helpful.


Dr Small

---

### Post by strabes on 2006-11-23
sudo apt-get update
sudo apt-get install soundconverter

---

### Post by Sam Lars on 2006-11-28
That's a nice program, but it doesn't do WMA files.  It's not even doing MP3 at the moment for me.
I've been looking for a program to do this same thing.  I did find one that is supposed to do it.
```
sudo apt-get install nautilus-script-audio-convert
```
It's supposed to use mplayer to decode the WMA files.  When I try it, it opens the decoding window, immediately closes it and opens the encoding window, and then claims it's done, though it's done nothing.  I got it to work for me briefly a while ago on a couple of files but other than that it's been frustrating.

---

### Post by Sam Lars on 2006-11-29
Okay, little update.  My program from above still isn't working for me, but I installed a bunch of gstreamer libraries and SoundConverter that strabes suggested is now converting a WMA file to Ogg.  I've got two WMA's I've been needing to convert.  SoundConverter only lets me add one of them, and converted it just fine.

---

### Post by denday on 2006-11-29
Why you want to convert wma to ogg?, If you just want to play them you can use xmms, it will play all audio type. including mp3, wma, and so on.

---

### Post by Sam Lars on 2006-11-29
That's a good question.  Rhythmbox even plays them.  I don't really know... I'd just rather have Ogg files and not WMA.  And I should be able to convert them.
I think it could be a problem with the file.  I used an application in Windows to convert most of them, but these two wouldn't convert.  Now one of them converted and one is left.

---

### Post by Skratz on 2006-12-03
is there a program that does it without using mplayer? (mplayer just doesn't work, gstreamer does)
*<edit>never mind, soundconverter does it.  I just found out I needed extra plugins to make it work.</edit>*


or is there a program that lets you edit id-tags of wma files?

---

### Post by Marsolin on 2006-12-03
[Perl Audio Converter]("http://linuxappfinder.com/package/pacpl") can convert WMA's to OGG.

---

### Post by Sam Lars on 2006-12-05
Okay, I tried soundKonverter, which was really nice.  It didn't work, and gave this error:
```
oggenc -b 112 -o "/home/matthew/Desktop/08 Your Song [Instrumental] {From the After the Storm Scene}.ogg" "/home/matthew/Desktop/08 Your Song [Instrumental] {From the After the Storm Scene}.wma.wav"
We received an error! Try to change the program for this file format and try renaming the files before converting.
Error:
ERROR: Cannot open input file "/home/matthew/Desktop/08 Your Song [Instrumental] {From the After the Storm Scene}.wma.wav": No such file or directory

```
I think I've looked at the Perl Audio Converter before... I'll see if I can get that to work.

---

### Post by defishguy on 2006-12-05
Try this website.  I haven't used it for audio, but it can do what you ask and it's performed well for what I have used it for.

[http://www.zamzar.com/](http://www.zamzar.com/)

---

### Post by Sam Lars on 2006-12-05
Thanks for that link.  That looks like a really cool site.  I tried converting from WMA to Ogg, and it gave me an upload error.  On the page about conversion types it said it didn't support WMA to Ogg, so I tried converting it to WAV.  I got the same error.  Something about an internal server error number 102.

---

### Post by adamkane on 2006-12-05
Perl Audio Converter (pacpl) is way too difficult to install. List the steps required, if you're going to suggest that one.

(Install konqueror, install pacpl service menu, install perl dependencies, enable/disable metatagging, ...).

If soundconvert or soundkonverter doesn't work, then you may need to install lame.

And of course this subject has already been covered on other threads.

---

### Post by Narasinha on 2006-12-20
I had looked for something to perform a similar audio conversion task, and found something that wokrs great for me. It is called "audio-convert-mod". It is a (GNOME) nautilus script that allows you to right-click on a file, and pring up a conversion dialog to go betwen various formats, WMA and OGG included. The home page is at [http://www.nongnu.org/script-wing/audio-convert-mod.html](http://www.nongnu.org/script-wing/audio-convert-mod.html)

Stats for this program (script):
Decode: (can go from) - AAC / MP4 / M4A
- MP3
- OGG
- MAC / Monkey's Audio / APE
- FLAC
- WAV
- Shorten
- WMA
- Any other mplayer-capable format

Encode: (can go to)
- AAC / MP4 / M4A
- MP3
- OGG
- MAC / Monkey's Audio / APE
- FLAC
- WAV

Requires: 
  bash
  zenity (for RPM users it is a part of the "gnome-utils" package)
  gawk
  file >= 4.16

Optionally requires at least one of the packages below: 
  mplayer		--for decoding WMA and any other mplayer-capable file
  lame 		--for MP3 conversion support
  id3tag		--for MP3 tagging
  vorbis-tools 	--for OGG conversion support
  musepack-tools	--for MPC conversion support
  flac		--for FLAC conversion support
  mac  		--for MAC (Monkey's Audio, or .ape) conversion support
  faac,faad2  	--for AAC / M4A / MP4 conversion support

---

### Post by mcglnx on 2006-12-20
I've had the same issue. I've installed Win32 codecs in /usr/lib/win32 and use Xine.
Works very well.

Hope that Helps,
M.

---

### Post by firebadger on 2006-12-20
You do realise though, that converting from one lossy format (wma) to another (ogg) will further reduce the quality of the files.  I certainly wouldn't do it without a very good reason.

---

### Post by mcglnx on 2006-12-20
Makes sense, I agree.
However, my player, an iAudio, does not read the WMA I got :(

---

### Post by Xiunix on 2007-03-15
I have been looking for a program to convert DRM .wma files to a more plyable format such as mp3 or what-not. I also have an iAUDIO, and it cannot understand the .wma OR the DRM support tags.

I tried the nautilus-audio conver site above, and the download is unresponsive...unless it's in the repos? Couldn't find the version if it was. More help on this would be greatly appreciated.

---

### Post by Marsolin on 2007-03-15
Unfortunately, DRM protected WMA files can only be played in Windows.  You can burn them to a CD and re-rip them into another format though.

---

### Post by chuckyp on 2007-03-15
ffmpeg should also be able to do this.

ffmpeg -i somefile.wma somefile.ogg

---

### Post by crimesaucer on 2007-03-16
I had a few songs on some scratched CD's that wouldn't rip properly in Grip or any other linux ripper that I tried. I even tried it with both CD Paranoia turned on and off.

Anyway, my Windows Xp could rip these files in WMA and Mp3.

Well, I already had my whole collection in ogg at a q6 variable bit rate, so I wanted to rip these last two songs in Windows in a WMA full bit rate, and then convert them into ogg vorbis around the same 192 kbps bit rate.

I found this script: A nautilus audio converter script

it's in Synaptic, and all you have to do is install it with whatever codecs you need like vorbis tools.

Then you take your song that is already ripped in WMA, and then right click on it, and select the "nautilus audio converter script", then just follow the easy to understand GUI directions.  Then I just renamed the song to match the way the rest of my ogg songs were and they play in order and in the same 192 variable bit rate using ogg.

---

### Post by gigaferz on 2007-10-08
thiis is soo awesome..just a script.... in a folder.... wow...

the best part is simple "it just works"

i gotta remove all those converters now..keep clean the system ...
I hope is built in the next release..

---

### Post by HermanAB on 2007-10-08
You can also use Sound Exchange together with find, to do conversions on a whole repository:

find . -name \*.wma -print -exec sox {} {}.ogg \;

Cheers,

H.

---

