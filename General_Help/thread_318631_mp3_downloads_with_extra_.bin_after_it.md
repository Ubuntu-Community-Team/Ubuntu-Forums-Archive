---
title: "mp3 downloads with extra .bin after it?"
date: 2006-12-14
forum: General Help
---

### Post by fezzik on 2006-12-14
Hello everyone. 

I have been downloading music on emusic.  When I download them in windows it is fine but in Ubuntu when I download it they come up with  song.mp3.bin  I have to remove the .bin for it to work in windows and in some things in Ubuntu.  It isn't a huge deal to remove it obviously but I would like to know how to have it download as just  a .mp3.  Please help.  

Thanks,
Chris

---

### Post by disabled_20220313 on 2006-12-14
I don't have that problem, I've downloaded from emusic.com with no problems.

I assume your using firefox and not anything else wierd?

Personally I don't know where to start, but knowing what browser your using would help other people to help you.

Good luck

---

### Post by fezzik on 2006-12-15
Right.  That would be good information wouldn't it?  I am using firfox 2.  Which is really nice by the way.  I don't have the download manager working from e-music.  I just have to do it song by song through firefox.  All I do is search for music find what I want click the blue square wait a couple of seconds and then I open the folder where I am saving them to and there it is song.mp3.bin all I have to do is remove the .bin and it works fine but I don't understand why it does it that way.  I figure there is a setting somewhere than I have messed up but I don't know.  It might be helpful to mention I am using Edgy Ubuntu 6.10.  Could this be a setting somewhere that I am just not finding?

---

### Post by disabled_20220313 on 2006-12-16
I personally don't have much of an idea, but the extra information that you've given might provide useful to someone else now.

Try and be patient and hope it works out...

Sorry, I can't be much more help.

---

### Post by fezzik on 2006-12-19
Hopefully someone out there has had this trouble.  Or someone knows something about it.  It is rather odd to me.  But everytime I download a song in Linux it adds the .bin.  Nothing major but I would like to fix it cause I do plan to do more downloading.

---

### Post by mahousaru on 2007-08-16
Bit of a late reply, but I couldn't find any solution in regards to this, so I thought I would share my experiences.  

I had the same problem too, when I was trying to download to a samba share. It didn't matter where I mounted the share FF would append a .bin to a mp3 or a .zip to a zip file.  It didn't happen on a local directory and Opera would save the files normally.

After trying many many things, I noticed that the only difference between a local directory and a samba mounted one was that it makes the files executable.  I set my umask and FF did the same thing to a local directory, so I remounted my samba shares with a fmask=640 and dmask=750 and no more problems.

I guess the first thing to try is to check the default file create writes of where ever you are saving to.

---

