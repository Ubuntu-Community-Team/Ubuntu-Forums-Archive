---
title: "Extracting music with Sound Juicer"
date: 2006-10-25
forum: General Help
---

### Post by randell6564 on 2006-10-25
Hi!
First off, for some reason I cannot extract my music CD's as WAV files. Sound Juicer will only extract them as Ogg or Flac. The Error is:
> Sound Juicer could not extract this CD.
Reason: Could not link pipeline
Dont know what this means, so I cant fix it!

So on to my question; is there a way to convert Ogg/Flac files to Wav or Mp3?
The reason that this is important to me is that your typical car and home CD players cannot play music burned in this format!
Thanks!

---

### Post by koshari on 2006-10-25
have you got the correct gstramer mp3 plugins?

---

### Post by koshari on 2006-10-25
To Rip CDs to MP3s, you can use Sound Juicer which uses gstreamer and the LAME mp3 encoder. The following should also work with other programs that use gstreamer: 1. Enable the universe and multiverse repositories. Then, install the gstreamer0.8-lame package to encode mp3s, and the gstreamer0.8-mad package to play them back (in Ubuntu 5.10). For Ubuntu 6.06, you will need to install the package gstreamer0.10-plugins-ugly-multiverse

2. Open Sound Juicer, click “Preferences” from the “Edit Menu”, click “Edit Profiles” and choose “New”. Call your new profile “MP3 Encoding”, or whatever else you feel like. :mp3-profile.png

3. Edit this profile and set Gstreamerpipeline to

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=160 ! id3v2mux
```

or

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192
```

(The last number specifies the quality of the file, a larger number means better quality, but larger file size. Optionally, you can change 160 to something else (e.g. 192, 256) if you want a specific (constant) bitrate other than the default of 160).

4. Additionally, if you are using Ubuntu 6.06 and would like to encode MP3s using the [WWW] “–preset standard”, the Gstreamer pipline should be set to audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001 ! id3v2mux

5. Finally, set File Extension to mp3, click the Active checkbox and then OK.

6. Restart Sound Juicer for the changes to take effect.

---

### Post by randell6564 on 2006-10-28
> **koshari said:**
> To Rip CDs to MP3s, you can use Sound Juicer which uses gstreamer and the LAME mp3 encoder. The following should also work with other programs that use gstreamer: 1. Enable the universe and multiverse repositories. Then, install the gstreamer0.8-lame package to encode mp3s, and the gstreamer0.8-mad package to play them back (in Ubuntu 5.10). For Ubuntu 6.06, you will need to install the package gstreamer0.10-plugins-ugly-multiverse

2. Open Sound Juicer, click “Preferences” from the “Edit Menu”, click “Edit Profiles” and choose “New”. Call your new profile “MP3 Encoding”, or whatever else you feel like. :mp3-profile.png

3. Edit this profile and set Gstreamerpipeline to

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=160 ! id3v2mux
```

or

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192
```

(The last number specifies the quality of the file, a larger number means better quality, but larger file size. Optionally, you can change 160 to something else (e.g. 192, 256) if you want a specific (constant) bitrate other than the default of 160).

4. Additionally, if you are using Ubuntu 6.06 and would like to encode MP3s using the [WWW] “–preset standard”, the Gstreamer pipline should be set to audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001 ! id3v2mux

5. Finally, set File Extension to mp3, click the Active checkbox and then OK.

6. Restart Sound Juicer for the changes to take effect.

You did it 'koshari'! Thanks SO much!!  I've been trying to digitaly archive my CD collection, but needed that collection as Wav or mp3 so that I could later burn it and have working CD's!

Thanks again!

---

### Post by dearephesus64 on 2006-11-08
I did get this to work on 6.06- thanks, sound juicer with gstreamer is a whole heck of a lot faster than kaudiocreator! (I have both desktops, KDE and Gnome)  

Only thing is, it didn't work for me with just the "gstreamer0.10-plugins-ugly-multiverse" package.  I had to install both the "gstreamer0.8-lame" package and the "gstreamer0.8-mad" package that koshari recommended for Hoary.  My "install packages until stuff works" strategy hasn't completely filled my hard drive yet, so lucky me.

This is what my gstreamer pipeline box looked like:

*audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=256 ! id3v2mux*

the LAME presets for extreme, insane, standard, medium (ex: preset=extreme) etc. don't work- XMMS can't decide how long the songs are, and Amarok thinks a four minute song is half an hour long.  The command line LAME presets worked fine with Kaudiocreator, but it's a lot slower.

---

