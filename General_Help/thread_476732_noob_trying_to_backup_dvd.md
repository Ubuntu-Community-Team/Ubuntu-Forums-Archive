---
title: "noob trying to backup dvd"
date: 2007-06-17
forum: General Help
---

### Post by clinto on 2007-06-17
I'm not a complete noob to linux, but to the following, I have little idea what I'm doing.

I just started getting into backing up my dvds. Unfortunately, I've been jogging over to Windows to use DVDshrink since I'm unsure how to use other programs.

So, I have the compressed files I want to copy, but I'm a little unsure how to go about doing so. So, I went here:
[http://gentoo-wiki.com/HOWTO_Create_a_DVD:Burn](http://gentoo-wiki.com/HOWTO_Create_a_DVD:Burn)

I was unsure if the information needed to be burned as an image or not. I originally thought I could just burn the AUDIO and VIDEO as is like a data disk. But, I guess it would make sense that it would need to be an image.

I tried using growisofs, but it tells me the command "emerge" can't be found. So, I'm guessing this is a process that Gentoo uses and doesn't really apply to *buntu? I'm using Kubuntu presently. I have Debian on the same machine though.

I think I'm going to jump back over to Windows real quick to make an .iso for now. It's just frustrating sitting here for hours trying to figure this crap out, especially when I don't have all that much time. *sigh* My Google searching skills need some improving I think. It's a little difficult to search for things you don't understand though:/

If anyone has some advice, would like to slap the noob out of me or has a good how-to you could point me to, I'll give you some lovin'.

---

### Post by orb9220 on 2007-06-17
You could always use dvdshrink thru wine. That is what I do. works just as fast when it runs in windows.

[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)
[https://help.ubuntu.com/community/DVDShrink](https://help.ubuntu.com/community/DVDShrink)

or install k9copy will compress a dvd movie.

---

### Post by clinto on 2007-06-17
Thanks. I can figure that out later though. What I need to know is how exactly to go about burning a dvd so that it may be viewed with a standalone dvd player. I have about a dozen on my harddrive that I need to get rid of.

This seems like it should be something real easy to figure out, but I'm having a hell of a time. 

So, I went back to dvdshrink and selected to compress as an image... and it gave me files with .001 .002 .003. I'm confused. Isn't it supposed to just make a single .iso file?

[ot]You know what's the worst part about being a noob? Knowing you are and being able to see your own stupidity. I don't know why I'm having such a hard time figuring this out on my own.[/ot]

---

### Post by orb9220 on 2007-06-18
I have that problem when I run windows and use dvdshrink and try to burn iso to a ext3 linux partition.
If I burn the iso in windows to a ntfs partition then it burns an iso file fine.

I have never figured it out why I when using ext3 IIfs for windows allows me to use my ext3 partitions in windows which works well for everything except creating a iso from windows program to a ext3 partition.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by clinto on 2007-06-18
Oh! That might explain things. Yeah, I have a separate partition set up as a storing volume using ext3(of course). So, I've been writing everything to this volume. It never crossed my mind that this could be the source of my confusion. I'll have to try it again tomorrow.

So, if I write it to Windows, I should be able to move the .iso over to the ext3 partition, correct? I'm sure, anyhow. I'll post once I figure out... and come across more problems:P

Thank you orb. I wouldn't have even considered that possibility.

---

### Post by orb9220 on 2007-06-18
> So, if I write it to Windows, I should be able to move the .iso over to the ext3 partition, correct? 

Correct or I when I need the space of the ext3 partition I have dvd shrink create a HD folder instead of iso and that works fine.

---

### Post by riger99 on 2007-08-11
I'm not too sure if this might help, but at least I hope it gives a start or some ideas/pointers? [Transcoding DVD audio track]("http://ubuntulinuxhelp.com/the-easy-way-save-dvd-audio-to-mp3/")

---

### Post by clinto on 2007-08-11
@riger99
That's good info, but it doesn't have to do with this topic. I was just concerned with figuring out how to back up a dvd under Linux. At the time I'd first posted this, I was unsure how to go about backing one up correctly, even in Windows. I learned that I wasn't making an image correctly. I figured it out using DVDshrink and DeepBurner. However, I still haven't been able to do it with Ubuntu. Thanks for the link though.

@orb
I haven't tried using DVDshrink through wine yet. That may be my next move. However, I've been messing around with numerous dvd-back-up applications, including k9copy, and have been unsuccessful with all of them. With k9copy, it would put out an .iso of only a couple MB and say it was finished. Maybe I was running into some encryption problems or something.

/off topic
I wonder if the .iso conflict has been addressed with the ntfs-ext2 driver. I guess it's not that big of a deal.

---

