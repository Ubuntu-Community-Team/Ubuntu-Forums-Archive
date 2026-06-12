---
title: "installed dvd-slide show via syn manager, can't find it"
date: 2008-06-23
forum: General Help
---

### Post by scotcella on 2008-06-23
I installed the dvd-slide show via the synapotics manager, which was sucessful, from what I can tell.

Now I can't find it even though I have tried using the terminal to open the program.

Any help appreciated!

---

### Post by caljohnsmith on 2008-06-23
> **scotcella said:**
> I installed the dvd-slide show via the synapotics manager, which was sucessful, from what I can tell.

Now I can't find it even though I have tried using the terminal to open the program.

Any help appreciated!

In Synaptic, if you right-click the package you installed, and then select "properties", you can click on the tab that says installed files. Look for the program name in a bin folder (under that list of installed files), e.g. /bin /sbin/ /usr/bin etc. That should help you find the program name, and then you can just run it from the terminal or look up its man page to learn how to use it.

---

### Post by mc4man on 2008-06-23
dvd-slide show is actually a shell script you run from cli. I only used it once so I could figure out how to make a looping dvd slideshow for someone. It was a bit of a pita to use at first and the gutsy ver. had a bug. (easily fixed by editing script). 
run these in terminal to get idea on how to run.
man dvd-slideshow
man dir2slideshow
I'll post back bug fix - need to look at script

edit: I believe in /usr/bin/dvd-slideshow you need to change these lines (if your ver. has bug
```
# setup audio parameters
if [ "$vcd" -eq 1 ] ; then
        ac3=0  # force mp2
        audio_bitrate=224k   [COLOR="Red"]<-[/COLOR]
	video_bitrate='1152'
        audio_sample_rate=44100
	mplex_type=1
	aspect_ratio="4:3"
	mpeg2enc_params="-v 0 -4 2 -2 1 -H -b 1150 -n n -s -f $mplex_type"
elif [ "$svcd" -eq 1 ] ; then
        ac3=0  # force mp2
        audio_bitrate=128k   [COLOR="Red"]<-[/COLOR]
	video_bitrate='4500'   
        audio_sample_rate=44100
	mplex_type=4
	aspect_ratio="4:3"
	mpeg2enc_params="-v 0 -4 2 -2 1 -H -b 2500 -n n -s -f $mplex_type"
else
        audio_bitrate=192k  [COLOR="Red"]<-[/COLOR]
	video_bitrate='3800'   
        audio_sample_rate=48000 
	mplex_type=8
	if [ "$widescreen" -eq 1 ] ; then
```
Your adding k iirc
easiest way to find is to open the file, search for bitrate and keep hitting ctrl+G

here is thread on looping slideshow, I'm sure your not interested in that but _some_ further use info
[http://ubuntuforums.org/showthread.php?t=744138](http://ubuntuforums.org/showthread.php?t=744138)

---

