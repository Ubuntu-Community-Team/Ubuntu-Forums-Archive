---
title: "grep doesn't search at all"
date: 2008-04-28
forum: General Help
---

### Post by Redsandro on 2008-04-28
Hi,

Long story short, my drive **MFT** was broke so it wouldn't work. But there is this big raw text file that I want back. I needed the drive for something else, so I created an image with **dd**. The image is, as is the drive, 40 GB.

I recall *multiboot* was mentioned in the article, dunno if it was capital *m*.

Image on portable drive, connected via USB, booted Ubuntu on my desktop and tried:

$ **grep -U -b *ultibot* ./sda.img > ./test.txt**

Took 20 minutes, found nothing. I know, that's because there's a typo in there.

I tried again with *ultiboot*, *ultibo*, *ltibo*, *"ultiboot"*, but they all complete in 1 second finding nothing. That's a lie, they cannot know that in 1 second. When I use *ultibot* again, it goes again for 20 minutes. Why?

I tried renaming the file, moving the file to another folder, rebooting the machine, dis- and reconnecting the drive in USB... I cannot grep anything besides the searchterm with a typo! It doesn't make sense!

Or does it?

---

### Post by NT4usB on 2008-04-28
did you try ```
grep -i
``` to make the search case insensitive?
How about searching a word you know and know is in there to see if the search will report anything?
Try it with a wildcard *****?

---

### Post by Redsandro on 2008-04-29
Very thanks for replying, but I think you're missing the point.

I have no trouble finding a correct search command, the problem is that **grep** won't search at all. It just sais *Not found* immediately, but a search in a 40 Gb file is supposed to take about 20 minutes, like it strangely did only the first time I used **grep**.

---

### Post by ghost_ryder35 on 2008-04-29
> **Redsandro said:**
> Very thanks for replying, but I think you're missing the point.

I have no trouble finding a correct search command, the problem is that **grep** won't search at all. It just sais *Not found* immediately, but a search in a 40 Gb file is supposed to take about 20 minutes, like it strangely did only the first time I used **grep**.
it may have cashed some search info into swap or ram so future searches can be faster.  if you use grep to search for a word you know is in there will it find it?

---

### Post by ebelog on 2008-04-29
> **Redsandro said:**
> Hi,
Image on portable drive, connected via USB, booted Ubuntu on my desktop and tried:

$ **grep -U -b *ultibot* ./sda.img > ./test.txt**


You used 'dd' to create a binary image of a full disk partition, and grep may not like the fact that you're running it against a binary file. I can't explain why searching for the typo takes longer, but to get it to work you could try mounting the image, and searching for the file you're looking for that way.

Try
```
mkdir /mnt/oldsda
mount -t ext3 -o loop ./sda.img /mnt/oldsda
find /mnt/oldsda -type f -name "*.txt" -exec grep -li ultiboot {} \;
```

---

### Post by Redsandro on 2008-04-29
> **ghost_ryder35 said:**
> it may have cashed some search info into swap or ram so future searches can be faster.  if you use grep to search for a word you know is in there will it find it?
No, so I think it made a wrong cache after the first search. Maybe it's not supposed to handle big files? Anyway, the cache persists after reboot so if you know a way to clean grep's cache that might do the trick.

> **ebelog said:**
> You used 'dd' to create a binary image of a full disk partition, and grep may not like the fact that you're running it against a binary file. I can't explain why searching for the typo takes longer, but to get it to work you could try mounting the image, and searching for the file you're looking for that way.

Try
```
mkdir /mnt/oldsda
mount -t ext3 -o loop ./sda.img /mnt/oldsda
find /mnt/oldsda -type f -name "*.txt" -exec grep -li ultiboot {} \;
```

I could grep inside ntldr to find "found", and that's also a binary file. But I can always try next time I am home.
But you think that works? Because the image is not just an ext3 image, it's a disk image containing 4 partitions. [ntfs][ext3][swap][ntfs] and the file is in the last ntfs partition, uncompressed. No EFS.

---

### Post by ebelog on 2008-04-29
> **Redsandro said:**
> 
I could grep inside ntldr to find "found", and that's also a binary file. But I can always try next time I am home.
But you think that works? Because the image is not just an ext3 image, it's a disk image containing 4 partitions. [ntfs][ext3][swap][ntfs] and the file is in the last ntfs partition, uncompressed. No EFS.

I thought you had made an image of a disk partition. It's definitely not going to work to try to mount a filesystem if the disk image is made up of multiple partitions. The logic may still apply ... if you could restore the disk image so you can see the contents, you'd probably have better luck than trying to grep through a 40 GB file.

---

### Post by ghost_ryder35 on 2008-04-29
> **Redsandro said:**
> No, so I think it made a wrong cache after the first search. Maybe it's not supposed to handle big files? Anyway, the cache persists after reboot so if you know a way to clean grep's cache that might do the trick.



I could grep inside ntldr to find "found", and that's also a binary file. But I can always try next time I am home.
But you think that works? Because the image is not just an ext3 image, it's a disk image containing 4 partitions. [ntfs][ext3][swap][ntfs] and the file is in the last ntfs partition, uncompressed. No EFS.
have you tried a reboot so then the cache is clean?  just a thought.  might work

---

### Post by Redsandro on 2008-05-01
> **ebelog said:**
> if you could restore the disk image so you can see the contents, you'd probably have better luck than trying to grep through a 40 GB file.I cannot overwrite the (new) disk at the moment. But also, since the MFT is broken, I cannot mount it anymore. I'm sure all the raw data sits there, it's just that there is no Master File Table anymore, so no one knows where what file is located.

> **ghost_ryder35 said:**
> have you tried a reboot so then the cache is clean?  just a thought.  might workYes, I said so in my first post :)> **Redsandro said:**
> I tried renaming the file, moving the file to another folder, rebooting the machine, dis- and reconnecting the drive in USB...but thanks for thinking with me. :) Maybe if I force a fs check, all caches will be purged. I'll try that too next time.

---

