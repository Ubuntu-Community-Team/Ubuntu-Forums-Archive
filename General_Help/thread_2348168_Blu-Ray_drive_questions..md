---
title: "Blu-Ray drive questions."
date: 2017-01-01
forum: General Help
---

### Post by CaptainMark on 2017-01-01
So I have a few questions, I have a collection of Blu rays that have been sitting up in my loft/attic since moving house over a year ago that I just have no where for them to go in the living room area, I was considering buying a blu ray drive so I can rip the films onto my pc which streams to my Kodi client behind the TV. I was considering something like this one [https://www.novatech.co.uk/products/components/opticaldrives/blu-raydrives/sn-406abbebe.html](https://www.novatech.co.uk/products/components/opticaldrives/blu-raydrives/sn-406abbebe.html)

So:

1. Does anyone have any experience with using Blu Ray drives on Ubuntu, do they work well?
2. If you have got Blu Ray experience on Ubuntu rate the ease of use 1-10.
3. If so have you used one to rip a movie to your hard drive?
4. Rate the ease of doing that 1-10.
5. What sort range can I expect the file sizes to be if I want a comparable quality to the original? (Doesn't have to be pixel perfect, but I don't want to low quality video to ruin my movie watching experience.)
6. Recommend a file format to go with. Right now I'm using .mkv files with H.264 video and vorbis audio, I'm quite out of the loop since I last ripped my DVD collection years ago and I could be using a obsolete format for all I know.


Many Thanks
Mark

---

### Post by oldrocker99 on 2017-01-01
Here's a good article about using Blu Ray devices on Ubuntu:[http://www.howtogeek.com/240487/how-to-play-dvds-and-blu-rays-on-linux/](http://www.howtogeek.com/240487/how-to-play-dvds-and-blu-rays-on-linux/).

---

### Post by Keith_Helms on 2017-01-02
I've had blu ray drives in 2 laptops and 2 desktops and they all work fine.  I think as far as the hardware goes, it's just another optical drive to Linux.

Playing blu rays on Linux is definitely not as easy as playing DVDs.  You will need some extra software to handle decrypting the discs, whether you're playing the disc directory or converting to another format.  Google that.

H.264 format is still a good option.  H.265 is available, but I get the impression it's still in a fairly early phase.  H.264 definitely is supported by more devices.  For example, I can serve the files up in mkv containers using something like ushare and both my TV and blu ray player will play them over the network.  I use AC3 for audio.  I doubt vorbis audio would be recognized.  If you're only care about your kodi setup, then use whatever audio you want and maybe give H.265 a try.

I usually downsample 1080p video to 720p, which is a good compromise between size and quality.  A movie at 720p takes up somewhere between 1.5GB and 3GB.  If you go with full 1080p, my guess would be to double those numbers.

---

