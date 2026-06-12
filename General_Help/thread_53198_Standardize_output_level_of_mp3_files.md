---
title: "Standardize output level of mp3 files"
date: 2005-07-30
forum: General Help
---

### Post by matthew on 2005-07-30
I have a shareware sound editor program on Windows called Goldwave which has several things I love and have not figured out how to do in Linux. For example, it can do batch processing with various effects or even standardization of output level for mp3, wav, and lots of other sound file types. I have used Audacity and it is a good program, but seems about 3 generations behind in its abilities, although I like it overall. I tried Rosegarden, but it crashed every time I ran it (several months ago...haven't tried it again lately so I don't recall what the problem was in any greater specifics). So, finally to the actual question:

In Goldwave on winxp I can do this:
1. select a file folder containg sound files such as a new folder containing the newly ripped mp3's or ogg's from one of my personal cd's
2. batch process every song so that the output level is -18db like a modern cd or -16db so it's a bit louder or whatever level I want to set. This is especially nice if you have an inexpensive portable mp3 player like mine that doesn't automatically normalize the volume as the songs change...without doing this I am constantly turing the volume up or down
3. when I have been processing files I recorded off of old vinyl records or cassettes I can dehiss, amplify, and remove pops all in one action and as a batch

Is there any program that can do this in Linux yet?

BTW, I haven't tried to install it using Wine yet as I would really like to go open source as my first choice.

---

### Post by SherlokK on 2005-07-31
Maybe Audacity, Rezound or Sweep would be relevant ?

---

### Post by flaming_monkey on 2005-07-31
The most impressive element that continues to impress me about the *nix communitie is ability to produce free open software for every task under the sun.

Volume Gain (both available from Synaptic):

* [Vorbis Gain](http://sjeng.org/vorbisgain.html) - setting the volume levels for ogg files. cd ~/music/album, vobisgain *.ogg

* [MP3 Gain](http://mp3gain.sourceforge.net/) - same as Vorbis Gain but for MP3's

For denoising/dehissing: 

* [Gnome Wave Cleaner](http://gwc.sourceforge.net/) 
*"The goals are simple -- denoise, dehiss and amplify audio files. With the use of libsndfile, you can now do this on a multitude of audio formats, wav, au, aiff, ..."*

---

### Post by matthew on 2005-07-31
flaming_monkey, thanks! Those look like they will do _exactly_ what I was looking to do. I had forgotten, but I already had mp3gain on my computer. I downloaded it through synaptic and forgot about it before I had a chance to play with it.

Say, do you know if either of these can be used as plugins in one of the more full-featured sound editors like Audacity? Just trying to save myself some steps if it is possible.

Thanks, Sherlokk for your input as well. I'll take a look at Rezound and Sweep, they seem pretty promising.

---

