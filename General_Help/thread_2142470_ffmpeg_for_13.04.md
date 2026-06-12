---
title: "ffmpeg for 13.04"
date: 2013-05-05
forum: General Help
---

### Post by Chelidze on 2013-05-05
[COLOR=#333333][FONT=Ubuntu Beta]I have a question how to get ffmpeg for ubuntu 13.04 I used to use this ppa 
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg) 

but as far as I understand 13.04 is not supported so any other way to get it ??[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]






Thank you in advanced[/FONT][/COLOR]

---

### Post by Frogs Hair on 2013-05-05
ffmpeg is included in the Gstreamer plugins and has been for all previous versions . It should be installed if you install the ubuntu-restricted-extras. Does the ppa offer something not included with the provided version?

---

### Post by Chelidze on 2013-05-05
Thank you for the reply 

Hm you are right there is a ffmpeg present on the system but is it any good ??

I wanted to run this commend 

```
ffmpeg -f "x11grab" -r:v "30" -s:v "1440x900" -i ":0+0,0" -codec:v "libx264" -crf "20" -me_method "epzs" -g "250" -subq "6" -keyint_min "25" -trellis "1" -bf "16" -threads "0" -b:v "700k" -bt "10000k" -r:v "25" "/home/levan/test.mkv"
```

and I got this error 

```
Unrecognized option 'codec:v'
Failed to set value 'libx264' for option 'codec:v'



```

I get errors like that a lot guess there is no codecs that ffmpeg can use ??
I have handbrake, kdenlive installed and they work fine but why does ffmpeg gives me errors ?? only encoding I could run was 

ffmpeg -i filewhatever output.ogg

---

### Post by mc4man on 2013-05-05
The ffmpeg binary supplied in 13.04 is  pretty old  & certainly long outdated ( 0.8.6 
So if using, then  use syntax it accepts, or use avconv instead or you could build your own more suitable FFmpeg
Probably would accept -vcodec

---

### Post by coldraven on 2013-05-06
You can compile it yourself using this guide, it takes about an hour to do all the packages listed.
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

---

### Post by scouser73 on 2013-05-06
> **Chelidze said:**
> [COLOR=#333333][FONT=Ubuntu Beta]I have a question how to get ffmpeg for ubuntu 13.04 I used to use this ppa 
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg) 

but as far as I understand 13.04 is not supported so any other way to get it ??[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]






Thank you in advanced[/FONT][/COLOR]

Open Terminal, then copy & paste the following command.

**sudo apt-get install ffmpeg**

Then enter your password & tap Enter.

---

### Post by Yellow Pasque on 2013-05-06
There seems to be a lot of confusion here. I doubt the OP really wants to build his/her own ffmpeg. S/he just needs to know that is that ffmpeg project got forked into off into libav and that is what Debian/Ubuntu now uses. 

[QUOTE=mc4man]use avconv instead[/QUOTE]
Yeah, that. Make sure libav-tools package is installed and use avconv. If you still want the ffmpeg binary or you are compiling programs looking for it, install libavbin-dev package. 

Technically, ffmpeg isn't really "deprecated", but libav devs like to think of it that way, and Debian/Ubuntu users should probably just think of it that way to make life easier.

[QUOTE=scouser73]ffmpeg is included in the Gstreamer plugins[/QUOTE]
Not really. There has been a package (gstreamer0.10-ffmpeg) that allows gstreamer to use ffmpeg codecs, but ffmpeg and libav are not part of gstreamer. The modern equivalent of gstreamer0.10-ffmpeg is gstreamer1.0-libav.

---

### Post by Yellow Pasque on 2013-05-06
Kind of off-topic, but for anyone with a cynical streak, google the libav/ffmpeg split. Silly humans abound...

---

### Post by Frogs Hair on 2013-05-06
There is more than one version in the 13.04 repository and the one provided with gstreamer appears to be much newer, but it is a media plugin.

---

### Post by Yellow Pasque on 2013-05-06
> **Frogs Hair said:**
> There is more than one version in the 13.04 repository
No, you're getting confused. You should think of the gstreamer-ffmpeg/libav as a wrapper. It's not a complete reimplementation of ffmpeg/libav.

---

### Post by northruptc on 2013-09-08
What is annoying here is that when I ask for ffmpeg I get libav instead which is not what I asked for. I could give two farts about the "split". When I ask for a package via its name then I want that specific package and not a fork the maintainer decided that I should use instead.

I understand this discussion might be a little old but the topic remains relevant.

As far as I am concerned there is a bug in the ubuntu ffmpeg specifically in the package name. If its not ffmpeg then using the ffmpeg package name is misleading and I am totally not amused with the redirection. I don't want to use libav (please don't give reasons why I should or shouldn't). I specifically asked for ffmpeg and giving me something else instead of what I specifically asked for is insulting to me (all of us) as a user.

---

### Post by Elfy on 2013-09-08
If you think it's a bug then report it as such at Launchpad.

Closed.

---

### Post by u2nTu on 2013-11-12
Struggled with this myself and found [a solution]("http://askubuntu.com/q/373322/165265") that I posted over on [askubuntu]("http://askubuntu.com/q/373322/165265") (same link).

As mentioned there, it's for 12.04.3, but believe it should work with 13.04 also. It's so easy to do (and undo), can't hurt to try it out.

Have now had a chance to put the real ffmpeg through its paces -- still can't find any problems.

Hope it works for you!



PS  Thanks to Elfy for re-opening the thread so this solution could be posted. Hope this works and Chelidze has a chance to mark it Solved before the window closes.

---

