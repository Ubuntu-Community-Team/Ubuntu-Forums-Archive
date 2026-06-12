---
title: "Burning a CD without any gaps in Ubuntu 16.04"
date: 2017-09-19
forum: General Help
---

### Post by jesus-freak on 2017-09-19
I have what should be a very simple problem but I have not been able to find a solution. I have some FLAC files, I want to burn them to a CD IN CD FORMAT so that it plays on a CD player. The problem that I am having is that for something like a live concert or the second side of Abby Road where there are different songs but they all blend together without gaps or spaces in between the songs. I can't seem to recreate that gapless effect with any of the Linux burning software. Brasaro, K3B and even Nero for Linux have all failed to make a gapless CD for me. Is there anyone who can help me with a guide or a detailed and easy way of accomplishing this?

---

### Post by jesus-freak on 2017-09-20
Any ideas?

---

### Post by Autodave on 2017-09-20
Hopefully someone else can help here. I have looking around awhile, but not getting really good info. I found an older post where the person claimed that k3b (which is the repositories) can do that very thing. That started me looking into it, but I have not found any real useful info. I also am not willing to install it to try it. Sorry! :-)

You may want to research it or possibly even install it and try it.

---

### Post by jesus-freak on 2017-09-20
I have installed K3B but I haven not found any way to burn without any gaps. If there is some process that I have to go through then it is not obvious and maybe someone can post it. I too have searched online but most of the posts regarding this issue are of no use because they are so old.

---

### Post by dragonfly41 on 2017-09-20
I have no experience in this subject.   But there are some tips in this thread ...

[https://arstechnica.com/civis/viewtopic.php?f=16&t=489206](https://arstechnica.com/civis/viewtopic.php?f=16&t=489206)

including using **shntool** for syncing track boundaries, which I see is in 16.04 Software Centre.

---

### Post by oldos2er on 2017-09-20
I've used k3b to burn audio CDS in the past successfully. I used DAO and burned at the lowest possible speed. 
No idea if this will help you or not.

---

### Post by jesus-freak on 2017-09-21
What is DAO?

---

### Post by howefield on 2017-09-21
> **jesus-freak said:**
> What is DAO?

"**D**isk **a**t **O**nce" as opposed to "**T**rack **a**t **O**nce"

Should be described in the K3B manual.

---

### Post by jesus-freak on 2017-09-21
Yeah, I tried that too, didn't work, still big gaps between songs.

---

### Post by howefield on 2017-09-21
Not sure it'll help much but I think I would import the flac files into something like Audacity, edit as appropriate and export to a file before writing to a CD.

---

### Post by Autodave on 2017-09-21
> **howefield said:**
> Not sure it'll help much but I think I would import the flac files into something like Audacity, edit as appropriate and export to a file before writing to a CD.

I had thought of that also. The problem with doing that though is that the recording would be one, very long recording: there would be no way of picking just one song out of it to listen to.

---

### Post by Dennis N on 2017-09-21
I remember this problem with Abbey Road Side B. To convert to digital, I recorded (using line in) to Audacity straight from a continous tape recording of the entire side B which I had made many years ago from the vinyl LP, then exported to a digital format, which can then be burned to CD if desired. You could also record directly from the LP to Audacity and do the same. 

I like it as one continuous CD track, but you could edit it into separate tracks with Audacity. If left as one continuous track, you can make a cue sheet if you want to jump to a particular spot.

---

### Post by peter_london on 2017-09-21
Nero can do this... There's a free trial version available. I did exctly this the other day :). I know it's
proprietary software, but still... works for now ;)

---

