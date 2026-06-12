---
title: "Ubuntu 14.04 - recordmydesktop"
date: 2014-10-28
forum: General Help
---

### Post by Timmoore001 on 2014-10-28
Just started to try and use it.

I've recorded this data:-

audio.pcm
img.out
specs.txt

now I think img.out can be turned into a video file with a .ogv video extention.

But I don't know how.

I'm lost (very)  as to what next.

Any thoughts very very welcome !

There seems to be nothing in the way of an idiots guide on internet.

It seems a most useful item of software !

A very puzzled.

Tim

---

### Post by CantankRus on 2014-10-28
I found one of the simplest screen recorders to use is 
[**_[COLOR="#B22222"]SimpleScreenRecorder[/COLOR]_**]("http://www.maartenbaert.be/simplescreenrecorder/")

---

### Post by Timmoore001 on 2014-10-29
Many thanks, I have installed it aok but not tested it yet.

Greatly appreciated.

Tim

---

### Post by Timmoore001 on 2014-10-29
Video works great but have not got audio to work yet.   

What are the simplest audio settings I can use ?  (simplescreenrecorder)

Tim

---

### Post by CantankRus on 2014-10-29
> **Timmoore001 said:**
> Video works great but have not got audio to work yet.   

What are the simplest audio settings I can use ?  (simplescreenrecorder)

Tim

Try settings as in pics.
To record the audio output of an application like Rhythmbox choose the "**monitor**" of the source as in pic1.

Then, as in pic2 choose **mkv** as the container and for audio use **vorbis** as the codec.

Clicking on preview as in third pic will show audio meters.
If a song is playing and you have chosen the correct monitor you will see the meters move.

(PS: I actually use an mp4 container and mp3 as the audio codec but it depends what you have installed.)

---

### Post by jhay2 on 2014-10-29
is your recordmydesktop settings same as mine ?

---

### Post by Timmoore001 on 2014-10-29
> **CantankRus said:**
> Try settings as in pics.
To record the audio output of an application like Rhythmbox choose the "**monitor**" of the source as in pic1.

Then, as in pic2 choose **mkv** as the container and for audio use **vorbis** as the codec.

Clicking on preview as in third pic will show audio meters.
If a song is playing and you have chosen the correct monitor you will see the meters move.

(PS: I actually use an mp4 container and mp3 as the audio codec but it depends what you have installed.)

Wow !  That is brilliant !    I will try it out tomorrow morning !

Many many many thanks !

:  ))))

Tim

---

### Post by Timmoore001 on 2014-10-30
I tried it out and still no sound.

I think part of the OS has died, so I'm going to re-install the os.

I keep all my data on a secondary drive so I just lose all the applications.

But simplescreen recorder is very elegant so I'm going to perservere !

Many thanks for letting me have a chance to try it !

:  )))

Tim

---

### Post by Tim036 on 2014-10-30
With a fresh install (I included the extra 32bit option) I got the same results plus a pile of OS errors.

I used MP3 an rytham box for sound.

I have a different symbol  on preview for a microphone, so I think we may have different versions of the application ?

I don't know how to check what the sound mechanism is on my PC but all the other applications cope ok.

A puzzled

Tim

---

### Post by Tim036 on 2014-10-30
With a fresh install (I included the extra 32bit option) I got the same results plus a pile of OS errors.

I used MP3 an rytham box for sound.

I have a different symbol  on preview for a microphone, so I think we may have different versions of the application ?

I don't know how to check what the sound mechanism is on my PC but all the other applications cope ok.

A puzzled

Tim

---

### Post by CantankRus on 2014-10-30
I don't know then???
I have a lot of stuff installed so I tested this by booting to a live 14.04 usb.

I enabled the universe and multiverse repos and then installed simplescreenrecorder using the guide from the ssr homepage.
[ATTACH=CONFIG]257603[/ATTACH]

I then opened an mp3 with rhythmbox where I was prompted to install plugins.
I marked them all and installed.
[ATTACH=CONFIG]257604[/ATTACH]

Played an mp3 with rhythmbox and recorded video with sound using settings shown earlier.
The different icon is just because I am not using the default icons.
Pic when using default icons...
[ATTACH=CONFIG]257606[/ATTACH]


Then when attempting to playback the screen recording using Videos I was again prompted to install a plugin
where after installation played fine.
[ATTACH=CONFIG]257605[/ATTACH]

When playing rhythmbox if you click on preview in ssr, is the sound meter reflecting the sound output?

What is your terminal output for...
```
pacmd list-sources | sed -n -e 's/device.description[[:space:]]=[[:space:]]"\(.*\)"/\1/p'
```

eg for me...
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **pacmd list-sources | sed -n -e 's/device.description[[:space:]]=[[:space:]]"\(.*\)"/\1/p'**
		Monitor of ClearChat Pro USB Analogue Stereo
		ClearChat Pro USB Analogue Mono
		[COLOR="#FF0000"]Monitor of Built-in Audio Analogue Stereo[/COLOR]
		Built-in Audio Analogue Stereo
```
This is the [COLOR="#FF0000"]source[/COLOR] I choose when I want to record what's  coming out my desktop speakers.
If i want to record what's  coming out my headphone speakers I choose **Monitor of ClearChat Pro USB Analogue Stereo**
To record my headset microphone I choose **ClearChat Pro USB Analogue Mono**

---

### Post by Tim036 on 2014-10-31
Many many thanks !  I was using my main computer.  And the OS was getting corrupted.  So I'm getting another hard drive and using that to continue my attempts to get simple desktoprecorder to work with sound.

many many thanks for your detailed support.

Its going to take a few days for the drive to arrive.

So I'll report back when I next get a chance to install it on the new drive.

thanks again,

Tim

---

