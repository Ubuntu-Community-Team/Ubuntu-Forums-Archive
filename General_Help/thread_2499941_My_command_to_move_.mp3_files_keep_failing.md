---
title: "My command to move .mp3 files keep failing"
date: 2024-08-16
forum: General Help
---

### Post by sofasurfer on 2024-08-16
I have an alias which I have used every day for a couple of years which is now failing.
The alias is ```
 alias mvmp3='cd Downloads; for f in *.mp3 ;do mv "$f" /media/daryl/"Clip Sport1"/Podcasts ;done; cd ~'
  
```
After I convert a file to a .mp3 this command moves .mp3 files from my download directory to my mp3 player. Lately though, it stops running without performing the action or it moves one (out of many) file and then stops running, and then when I check on what it did I see that the one file that moved is gone.

Here is what I am left with as an error ```
  $ mvmp3
mv: cannot create regular file '/media/daryl/Clip Sport1/Podcasts/LIVE TV and Crowd GOES WILD.mp4.mp3': Input/output error
mv: cannot create regular file '/media/daryl/Clip Sport1/Podcasts/WHOSE LAND IS IT.mp4.mp3': Input/output error
 
```

Any ideas why this is happening? As I said, this command has work well for a looong time.

---

### Post by sofasurfer on 2024-08-16
I tried something different. I put my memory card in a card reader and plugged it into the computer. I was able to transfer my files with no problems...so far. So I am guessing that my usb cable is bad, the jack on my mp3 player is bad or my mp3 player itself is bad in that it will not accept file transfers. So my next step would be to get a new usb cable and if that doesn't help then I guess I need a new mp3 player. Not a bad geal since this mp3 player has never seen a day of non-usage (listening, transfers and cord insertions) in around 10 years.

---

### Post by TheFu on 2024-08-16
Your alias makes all sorts of assumptions that may not be true.

Rather than 
```
cd Downloads
```
Use 
```
cd ~/Downloads
```

Also, I'm not a fan of hardcoded paths, but sometimes it is necessary.

I'd also use 
```
"/media/daryl/Clip Sport1/Podcasts"
```

When I/O errors are seen, that usually means the file system is corrupt and fsck is needed.  If that doesn't fix it, reformat the entire partition with the file system you need.  In general, it is better to avoid foreign file systems like NTFS, exFAT, FAT32.  Keep that in mind.

---

