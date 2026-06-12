---
title: "get-iplayer - how to get lower resolution downloads"
date: 2016-09-03
forum: General Help
---

### Post by grey1beard on 2016-09-03
I'm now finding that get-iplayer is trying to get downloads that are about x4 the size that I expect. A 1 hour program coming in at about 2000Mb, instead of 500Mb.
I assume that this is something that has changed in the last few months since my last use, and while I'm sure there is a method of selecting a lower res version, and that if I was familiar with the man pages, I could work it out, I would think it most kind if someone could lead me by the hand to sort it out.

Regards all,
John aka grey1beard.

Looking at man pages - the current download mode is hvfhd1, but I can't identify which mode I should be using. It will only be shown on either a 15" laptop screen or a 22" monitor.

---

### Post by howefield on 2016-09-03
You could use the --info option to identify the potential download modes, then use the --modes option to download.

Eg.. getting the info and sending to a text file to make it easier to browse, (there is a huge amount of infor in addition to the below, have just picked this out for illustration)..

```
hugh@xenial-laptop:~$ get_iplayer --info 1609 > ~/test
get_iplayer --info 1609 > ~/test
modes:          default: flashhd1,flashhigh1,flashhigh2,flashlow1,flashlow2,flashstd1,flashstd2,flashvhigh1,flashvhigh2,hlshd1,hlshigh1,hlshigh2,hlslow1,hlslow2,hlsstd1,hlsstd2,hlsvhigh1,hlsvhigh2,subtitles1
modes:          shortened: flashhd1,flashhigh1,flashhigh2,flashlow1,flashlow2,flashstd1,flashstd2,flashvhigh1,flashvhigh2,hlshd1,hlshigh1,hlshigh2,hlslow1,hlslow2,hlsstd1,hlsstd2,hlsvhigh1,hlsvhigh2,subtitles1
modesizes:      default: flashhd1=329MB,flashhigh1=111MB,flashhigh2=111MB,flashlow1=55MB,flashlow2=55MB,flashstd1=71MB,flashstd2=71MB,flashvhigh1=207MB,flashvhigh2=207MB,hlshd1=349MB,hlshigh1=117MB,hlshigh2=143MB,hlslow1=58MB,hlslow2=51MB,hlsstd1=75MB,hlsstd2=83MB,hlsvhigh1=219MB,hlsvhigh2=264MB,subtitles1=33KB
modesizes:      shortened: flashhd1=329MB,flashhigh1=111MB,flashhigh2=111MB,flashlow1=55MB,flashlow2=55MB,flashstd1=71MB,flashstd2=71MB,flashvhigh1=207MB,flashvhigh2=207MB,hlshd1=349MB,hlshigh1=117MB,hlshigh2=143MB,hlslow1=58MB,hlslow2=51MB,hlsstd1=75MB,hlsstd2=83MB,hlsvhigh1=219MB,hlsvhigh2=264MB,subtitles1=33KB
hugh@xenial-laptop:~$
```

Once you have a mode that you want it can be added to your preferences to be used as default with..

```
get_iplayer --prefs-add --modes=xxxx
```

---

### Post by grey1beard on 2016-09-03
Thanks Howefield, I now am getting a handle on it.
I'm now downloading with hvfvhigh mode, which is about the size I would expect.
Regards
John

---

### Post by ajgreeny on 2016-09-03
See post #3 of [https://squarepenguin.co.uk/forums/thread-1027-post-4649.html#pid4649](https://squarepenguin.co.uk/forums/thread-1027-post-4649.html#pid4649)
The default download mode has changed and now means huge file sizes if you stick to the default.

Unless I specifically need the very high definition for recordings I now use command ```
get_iplayer -g --tvmode=better ####
```by making use of an alias, which gives file downloads of the older, smaller size which is good enough for most viewing that I do. 
The better quality is always available if needed.

---

### Post by howefield on 2016-09-03
> **grey1beard said:**
> I'm now downloading with hvfvhigh mode, which is about the size I would expect.

Cool, glad you are getting what you want.

You are correct in that something changed and thanks to ajgreeny for the link.

---

