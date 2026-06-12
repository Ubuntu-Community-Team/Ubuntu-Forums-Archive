---
title: "Is it possible to strip away a folder, and leave subfolders intact?"
date: 2013-06-10
forum: General Help
---

### Post by heyho on 2013-06-10
I hope my question makes sense.

I have a 32gb sd card in my car stereo, which has a folder on it named "music", in which are subfolders "A", "B", "C" etc, containing the relevant artists and albums etc.

What I would like it to have is all of the subfolders on the root of the card, and not in a folder named "music", but preferably without transferring everything off of the card, and then back on, as I only have a slow card reader, and there is approx 25gb of data on the card itself.

So essentially I'd just like to strip away the "music" folder, and leave the subfolders on the root of the cards, if this is at all possible.:)

---

### Post by cool110 on 2013-06-10
just cd into the into the music folder on the card and run mv * ../

---

### Post by HiImTye on 2013-06-10
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
```
cd /path/to/card
mv -R Music/* .
rm -R Music
```

---

### Post by papibe on 2013-06-10
Hi heyho.

It is very possible.

Just move the content of the folder to the root level:
```
shopt -s dotglob 
cd /path/to/music
mv -iv * /path/to/cardroot
```
If there's a file or subdirectory that has the same name as as one on the root directory, you'll be warned with a message, and it won't be moved. For example, if you have a subdirectory named music, under music itself you'll be warned with this message:
```
mv: cannot move `music' to `/path/to/cardroot/music': Directory not empty
```
In this case you'll have to move it manually with another name:
```
mv -iv /path/to/music/music  /path/to/cardroot/othermusic
```
To check the directory is absolutely empty run this:
```
ls -la /path/to/music
```
The expected result should be something like this
```
drwxrwxr-x 2 youruser youruser 4096 Jun 10 15:27 .
drwxrwxr-x 4 youruser youruser 4096 Jun 10 15:27 ..
```
Then you can even remove music:
```
cd /path/to/cardroot
rm -rf /path/to/music
```
That would be it.

Other considerations: Moving your music it may means that your car player might need to rescan all your music again.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Vaphell on 2013-06-10
you should be able to do it via gui easily by selecting everything in music dir (ctrl+a), cutting it (ctrl+x) and pasting it in card's root dir (ctrl+v). Move operations within the partition update only filesystem info about the moved items themselves (top level subdirs/files in this case), there should be no data transfer involved. Empty music dir can be deleted aftewards

---

### Post by heyho on 2013-06-11
Thanks to all who have answered, I will update with the results later today once I am at home.

---

