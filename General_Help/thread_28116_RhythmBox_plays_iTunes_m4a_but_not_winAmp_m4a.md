---
title: "RhythmBox plays iTunes m4a but not winAmp m4a"
date: 2005-04-18
forum: General Help
---

### Post by pietro_spina on 2005-04-18
hey y'all,

Here's the quick version... 
I can play *.m4a files ripped with itunes but not ones ripped with winAmp in Rhythmbox...
Any thoughts as to why this might be? and how to get Rhythmbox to recognize them?

I know some of you are itching to tell me to just use beep or xmms or vlc or your equally fantastic player... read on...

And the long version goes something like this...
Currently running Hoary with debian-marillat/ unstable main
I have pinned according to this item 2.2 here [http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)

I had to force install
libfaad2-0  2.0.0-0.5(unstable) and
libfaac0    1.24-0.3 (unstable)
in order to get gstreamer0.8-faad and gstreamer0.8-faac to install from marillat.

There is nothing else special installed thought in the past I have tried some other players... below is a chart of my success... All in all, pretty good for compatibility...

```

_________________________________
|played in  |     ripped in     |
|           | iTunes  | winAMP  |
|           |-------------------|
|iPod       |  yes    |  yes    |
|winAMP     |  yes    |  yes    |
|XMMS*      |  yes    |  yes    |
|BMP*       |  yes    |  yes    |
|VLC        |  yes    |  yes    |
|Rhythmbox  |  yes    |  nope   |
|_______________________________|
  *plug-in installed

```

so have I done something so obviously wrong that it's painful to even tell me or what?

also, how about that text table.. pretty sweet eh?

---

### Post by kassetra on 2005-04-18
[QUOTE=pietro_spina]
I can play *.m4a files ripped with itunes but not ones ripped with winAmp in Rhythmbox...
Any thoughts as to why this might be? and how to get Rhythmbox to recognize them?
[/QUOTE]

When you ripped the files in winamp - were they originally in iTunes?  Have you played any of the winamp ripped .m4a in either winamp or iTunes?

- winamp and iTunes do *NOT* get along well when it comes to .m4a files.

---

### Post by kassetra on 2005-04-18
One other note is that winamp and iTunes each use their own specific m4a codec... and according to the audiophiles I know, the m4a codec in winamp has compatibility issues.

---

### Post by pietro_spina on 2005-04-18
> - winamp and iTunes do *NOT* get along well when it comes to .m4a files.
so I gather from the abundance of grief being shared on on these and other forums...

K-
the winAmp rips were straight from my own CD's (i'm not a pod person yet...But my birthday is right around the corner... grin) The iTunes files were rips from CDs as well... I don't have the iTuns software but I watched it happen. (rips of the same CD by the way...so that's not the glitch)

I can play both rip methods in most players, (see the table above) just not in Rhythmbox.(sad)  I like BMP and I'm using it right now. Though, I'd prefer to use rhythmbox. I just thought I'd see if anyone else came across this behavior?

p

---

### Post by pietro_spina on 2005-04-18
so in your professional opinion, the winAmp Lama whipped my ass? (grin)

are there not standards for these things? oh wait here it is...
> MPEG 4 Audio on the other hand uses an Internationally approved MPEG/ISO standard. This MPEG 4 Audio standard exists to enable your audio files to play properly on multiple platforms and on various hardware and software players for years to come.
sure... hehehe

Any thoughts on a fix? I'm thinking I might download the iTunes software and see if I can somehow "clean" my winAmp rips...

---

### Post by pietro_spina on 2005-04-19
I read that lots of the incompatibility issues between iTunes and winAmp were revolving around the tags and tag manipulation. So I decide to try re-tagging some of the files. 

I wiped out and re-wrote the tags for a couple of songs using both "mp3tag" and Tag&Rename in windows. (this supposedly solves the corruptibility issues for many) but not my playability issue...

So now I give iTunes software a shot and it turns out I need admin privileges… well that’s not going to happen for something this trivial.

Looks like I’ll be breaking out the old Win2000 CD if I want to give that a try…


arrg...

---

