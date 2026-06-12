---
title: "Difference between cache and buffering cache on the HDD"
date: 2014-07-25
forum: General Help
---

### Post by joan_carles2 on 2014-07-25
Well. As you may know in the HDD there is what we call cache. 16MB, 64MB and so on.

My question is what this cache really stores? I think that for a long time I've confusing the real cache memory and the buffering cache.

And then where is really made the buffering cache of my HDD? I guess it's in the RAM memory of my computer. Correct?

---

### Post by mooreted on 2014-07-25
There are all kinds of caches in computer systems. Basically, it's a temporary place to store a bunch of instructions. The HDD controller copies instructions to the cache so that they can be processed quickly in batches. Without caching the computer would have to read each bit of data from the hard drive every time it wanted to get more data. Hard drives are hundreds of times slower than memory, so it's quicker to read the data from a cache. Your HDD cache is actually part of the hard drive controller not your onboard RAM, though there are technologies that can use RAM as an extra HDD cache.

[http://computer.howstuffworks.com/cache4.htm](http://computer.howstuffworks.com/cache4.htm)

[http://en.wikipedia.org/wiki/Disk_buffer](http://en.wikipedia.org/wiki/Disk_buffer)

---

### Post by joan_carles2 on 2014-07-25
From my understanding in linux all the ram in your system works as a buffer cache. And commands like hdparm, read the speed of the buffer cache in the ram of your system and not in your HDD cache.

so in Linux there are the buffer cache in your ram memory and then there is another cache in the HDD (just another ram memory) that maybe stores position of some information in order to locate faster the information.

thats my understanding, and I don't know if it's correct. I've been looking information in google. But the information it's just confusing.

---

### Post by mooreted on 2014-07-25
It is pretty complex stuff. Linux also uses a type of RAM disk in the form of tmpfs, or "Temporary File System" that loads data into RAM for quicker access. There are swap files, memory paging, memory mapping, swaping and caching algorithms. Basically the operating system wants to get as much repetitive data into RAM as it can so it doesn't have to keep reading from the hard drive.

In very simple terms: You come back from the store with a trunk full of groceries. You can grab one bag, take it into the house then go out and get another bag and take that into the house and repeat that process until all the bags are in the house, or you could grab as many bags  as you can each trip and reduce the number of trips out to the car you have to take.

Of course it gets really complex after that with write-behind cache read-through cache, and on and on. It the sort of thing people get master's degrees in.

---

### Post by mooreted on 2014-07-25
Oh, and buffer and cache are used interchangeably. There is a kind of academic difference that is summarized in this post:

"Buffers are associated with a specific block device, and cover caching of filesystem metadata as well as tracking in-flight pages. The cache only contains parked file data. That is, the buffers remember what's in directories, what file permissions are, and keep track of what memory is being written from or read to for a particular block device. The cache only contains the contents of the files themselves."

[http://stackoverflow.com/questions/6345020/linux-memory-buffer-vs-cache](http://stackoverflow.com/questions/6345020/linux-memory-buffer-vs-cache)

---

### Post by joan_carles2 on 2014-07-26
More or less I pick it up. However on HDD specification the manufacturers use to detail buffer cache 16MB. or 64MB ....

But why they only specify buffer cache? Why they don't specify cache as well?

---

### Post by mcduck on 2014-07-26
The cache you see mentioned in a hard drive's specs is a different thing from the buffers/cache your operating system uses.
The specs talks about the cache memory integrated on the drive itself, used by the driver's controller (regardless of what OS you run or it the OS does any of it's own caching and buffering to RAM).

The main use for the cache on the hard drive itself is to allow the drive controller to collect a bunch of files used recently (in the same way the OS might cache data to RAM), but even more importantly it allows the drive to collect files that are intended to be written on the disk, and then order the writes in a way that reduces the amount of moving the read/write head around the disk surface.

---

