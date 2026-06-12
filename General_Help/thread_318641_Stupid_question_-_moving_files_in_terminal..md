---
title: "Stupid question - moving files in terminal."
date: 2006-12-14
forum: General Help
---

### Post by Roasted on 2006-12-14
I seriously have no idea what I'm doing wrong. I just decided I wanted to move files from my shared limewire directory over to where I store my music videos.

The music video is currently in /home/jason/Shared.
I want it to be in /home/jason/videos.

The video name is Crossfade - Cold (acoustic).

How do I move it? I tried quite a few options and even did a man mv and it helped, but I still couldn't figure out what I was doing wrong. I just figured I'd ask so I can walk away from this... ](*,)

---

### Post by EarlGrey on 2006-12-14
Did you put the name in quotationmars?

---

### Post by taurus on 2006-12-14
```

mv  "/home/jason/Shared/Crossfade - Cold (acoustic)"   ~/videos

```

---

### Post by pay on 2006-12-14
Try ```
mv /home/jason/Shared/Crossfade\ -\ Cold\ (acoustic) /home/jason/videos/Crossfade\ -\ Cold\ (acoustic)
```

---

### Post by Roasted on 2006-12-14
When I saw what Taurus wrote, I figured I'd just type out the long way.

What I typed in was this:

mv  "/home/jason/Shared/Crossfade - Cold (acoustic)"   /home/jason/videos

All it did was rename the video to "videos" and it was in the /home/jason dir... 

Why is this? Was it that important to use the ~/?

---

### Post by taurus on 2006-12-14
~/ means your $HOME directory, /home/jason...  Don't you already have a videos directory?

```
ls -la ~
```

---

### Post by hikaricore on 2006-12-14
Yea if you don't currently have a directory named videos and you type anything else after the directory you're moving it to (aka a folder that doesn't exist), your file will get renamed, that's just how it works.  Your bash terminal doesn't know what you're trying to do, it just does exactly what you tell it to do, sometimes quite literally.

---

### Post by Roasted on 2006-12-14
That's what's strange... I DO have a videos directory in "jason".

In Jason's folder I see music, videos, pictures, shared, finished (torrents), and all kinds of other stuff. I DO have a folder named "videos" there... that's why I'm confused. All it did was rename the music video to "videos" and put it right beneath my "videos" directory.

---

### Post by taurus on 2006-12-14
> **Roasted said:**
> That's what's strange... I DO have a videos directory in "jason".

In Jason's folder I see music, videos, pictures, shared, finished (torrents), and all kinds of other stuff. I DO have a folder named "videos" there... that's why I'm confused. All it did was rename the music video to "videos" and put it right beneath my "videos" directory.

There you have it.  You moved it from ~/Shared to ~/video but there is no video directory.  That's why it got the name video...

---

### Post by Roasted on 2006-12-14
> **taurus said:**
> There you have it.  You moved it from ~/Shared to ~/video but there is no video directory.  That's why it got the name video...

Um, what? There IS a videos directory... There's no reason for it to get renamed, it should of went IN the directory.

---

### Post by Afief on 2006-12-14
shouldn't it be
```
mv "/path/to/some/file/file.avi" "/new/path/file.avi"?
```

the reason the file was renamed is probably that there was no slash at the end of the destenation, which the CLI understood as the new _name_ of the file, not the new _folder_ where you want the file.

It should work like this
```
mv  "/home/jason/Shared/Crossfade - Cold (acoustic)"   ~/videos/ 
```

Hope it helps

---

### Post by hikaricore on 2006-12-14
Also if your directory is named "Videos" and you typed "videos" when you moved the file instead, it will not move the file correctly as most linux file systems allow for naming such as this, unlike fat and ntfs file systems.

---

