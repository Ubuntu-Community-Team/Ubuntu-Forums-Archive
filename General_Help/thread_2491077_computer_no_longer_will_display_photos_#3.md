---
title: "computer no longer will display photos #3"
date: 2023-09-25
forum: General Help
---

### Post by jgw on 2023-09-25
This is 3 weeks and this has now happened to me on another machine. Here is what I have so far:
    This computer has a new ubuntu 22.04.3 (+ new update). It thinks that a .jpg file is a text file and its empty.

    [code]
    file India-050.jpg
    India-050.jpg: empty

    Same file - other computer:
    file India-050.jpg
    India-050.jpg: JPEG image data, JFIF standard 1.01, resolution 340x1560, components 3(DPI), density 72x72, segment length 16, baseline, precision 8, 2
    [code]

    Find system info here: https://termbin.com/bw4n

    I have tried to have a different programs (like gimp and shotwell which think they are text files too) to get it to show me the image of the .jpg file and got nothing.

    This happened to me on another computer and I remember that it just stopped doing this and started to recognize jpg files. I have no idea of what I did or what the machine did.

    I did a google search and this seems to be a regular problem. I also did a search here but couldn't find anything that helped.

    Anybody have any ideas on this one? 


    Memory: 24gb
    Processor: AMD® Fx(tm)-6300 six-core processor × 6
    Graphics: GeForce GT 440/PCIe/SSE2
    OS: Ubuntu 22.0.04.2 Gnome: 42.5

---

### Post by The Cog on 2023-09-25
Can you post the output of these commands on the two computers please:
```
ls -l India-050.jpg
md5sum India-050.jpg
```

---

### Post by jgw on 2023-09-25
Thank you for the reply......

cd wallpaper
~/wallpaper$ ls -l India-050.jpg
-rw-rw-r-- 1 greg greg 0 Aug 21  2001 India-050.jpg

~/wallpaper$ md5sum India-050.jpg
d41d8cd98f00b204e9800998ecf8427e  India-050.jpg

---

### Post by The Cog on 2023-09-26
Well the file is indeed empty. Length 0 bytes, and the md5sum matches that of an empty file.
So the problem is not that the PC will not display pictures, but that somehow those files are being overwritten.

One thing that confuses me is that the date on that file is August 2001, as though it hasn't been changed for 22 years. That suggests that either it's been put there from an old archive, or the filesystem is corrupting files.
Corrupting filesystem seems unlikely to me, especially on two different computers.
Are you sure that file did ever contain an image - that it hasn't always been an empty file that you've only just looked at? If so, I can't think how that can be happening I'm afraid.

---

### Post by jgw on 2023-09-27
Thank you for the reply..........

I just installed ubuntu 22.04.3 on a new system.  I then copied the file to there and checked it and the entire file was bad.  

I just went to another machine, where the photos are seen, and copied the file to a memory stick.  I then checked it and it was fine.  Then I moved the stick to the problem machine, I checked the folder to see it it was still working and it was.  I then deleted the file that was there  and then copied the new one to that machine.  And, sigh, now everything is working.  That being the case its the copies that are screwing up and not the system!  This also means I am a lousy tester and I apologize for wasting your time.  

Life is just a bowl of cherries - with pits?

---

### Post by jgw on 2023-09-27
<sigh> 

I decided to take a hard look at the photos in the file and about 75% of them are bad.  Went back to the source file and the folder was just fine and all the photos were dandy.  I have no idea what is going on.  I marked this as solved, it wasn't and I am not having a real good time right now.

---

### Post by The Cog on 2023-09-28
It's good that you know what the issue is, and you can recover the pictures.
One thought - after copying files, it is possible the the GUI looks as though it has finished even though the copying is still happening from cache in the background. Always use the proper eject buttons on the file manager rather than just pull the stick out, and preferably use the command **sync** before pulling it as well - sync won't return until all the write cache has been fully written out.

---

### Post by jgw on 2023-09-28
I was thinking about that.  As a result, when copying, I waited about 5 minutes after it said it was done transferring stuff.  When I took a look at what was transferred some were good some were not.  Today I went back in to see what they were and, today, they were all bad.  I have no clue what the heck is happening.  I didn't have much time today to study on it but, tomorrow I am going to take another long look.  

Its interesting.  I suspect that at least part of my problem is assuming transfers are done when they are not.  The machine that I am writing this has the folder which I am transferring around.  Its supposed to be holding something around 330 pictures.  The folder was taken from another drive where I have all my photos.  Some of which are over 50 years old.  They are all there and are just fine.  

I'm going to spend some time trying to figure this one out.  

The fact, however, is that the system too is at fault as photos I know are just fine will not display and the system itself is finding fault with jpg files that I know are just fine.  

Mysteries abound?

---

