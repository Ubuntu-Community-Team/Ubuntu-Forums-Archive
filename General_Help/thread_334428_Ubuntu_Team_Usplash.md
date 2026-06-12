---
title: "Ubuntu Team Usplash"
date: 2007-01-08
forum: General Help
---

### Post by Steve S. on 2007-01-08
I've been playing with the Edgy custom usplash (as [noted here at this link]("http://www.ubuntuforums.org/showthread.php?t=323520")) and came up with one that I thought was pretty good, and thought others might want to use it.  But it's my first time posting a new thread on something I put together, so be nice to the relative (in this case) noob.

Oh, and I've only tried it on 1024x768, but it should work on most resolutions...I used the original Edgy usplash as a template (as noted in the thread mentioned above).

I'll explain how to install it manually (as I did), but I recomend that you go out and find a thread on Start Up Manager (SAM), if you like to modify your usplash (that boot screen that shows the words and what's being loaded at startup).  Using SAM makes life much easier when it comes to usplash.

Anyway, download the tar.gz file I've attached, save it somewhere.  Then extract it where-ever you like (I find using the gui and double clicking and extracting to be easiest, but to each his/her own).  

Ones you have the usplash-ubuntuteam.so extracted, copy it to the usplash directory:
```
sudo cp /where/thefileis/usplash-ubuntuteam.so /usr/lib/usplash/usplash-ubuntuteam.so
```
obviously substituting the directory where you saved it, where it is to be copied from.

Then you need to add the file to the alternatives list.  I find this long command works:
```
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-ubuntuteam.so 10
```

Then you need to pick this file as the alternative you want to use.  Like I said, this is much easier with SAM, but here's how you do it manually:
```
sudo update-alternatives --config usplash-artwork.so
```
and pick the alternative that you just added, in this case usplash-ubuntuteam.so.

Then run this to get the usplash up and running:
```
sudo update-initramfs -u

```

By the way, this procedure has worked for me pretty consistently in edgy on most any good usplash that I want to put in there.

Hope you like it!

I'm attaching the tar file and a moch version of what it looks like.  I think it looks much better with the words and, to be honest with you, haven't really tried it without.  Post back if you found this thread helpful and/or if you want the source code...I can post that to if requested.

---

