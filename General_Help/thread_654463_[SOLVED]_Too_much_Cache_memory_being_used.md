---
title: "[SOLVED] Too much Cache memory being used"
date: 2007-12-31
forum: General Help
---

### Post by TidusBlade on 2007-12-31
I know what it does and all, and of course I dont want that RAM to be used for nothing, but I deal with loads of big files, over 1GB and sometimes even above 4GB, so cached memory is being used up too much, and then it starts using the Swap, which slows down everything :( I have 2GB RAM, which I consider pretty good for Kubuntu. Is there any way to configure how the cached memory is used or anything, or would it be better to just leave it alone.
Any help or suggestions would be welcomed, Thanks!

---

### Post by SOULRiDER on 2007-12-31
I think its better to leave it alone, you can change some settings but the wrong settings could cause bad trouble.

---

### Post by mcduck on 2007-12-31
Cache usage shouldn't make you use any more swap than what you'd need without it. (As the data from cache is dropped if your programs need more memory) And when working with files as big as that, you are going to use swap anyway.

But if you want, swap usage can be tuned in Linux:

You can use the following command to adust the swappiness on-the-fly:
```
sudo sysctl -w vm.swappiness=10
```
The number can be anything between 0 and 100, 0 means that swap is never used and 100 means that swap is used as much as possible. '10' is a bit low for desktop machine but might be nice for laptops to save power (with less hard disk usage).

When you find a setting you like, you can make it permanent by adding a line with "wm.swappiness=10" into /etc/sysctl.conf.

(But, like I said, when working with files that are bigger than what can fir into your RAM you _will_ be using swap, no matter what. Or just fail to even open the file it there isn't any swap available)

---

### Post by chrisccoulson on 2007-12-31
> **mcduck said:**
> Cache usage shouldn't make you use any more swap than what you'd need without it. (As the data from cache is dropped if your programs need more memory) And when working with files as big as that, you are going to use swap anyway.

But if you want, swap usage can be tuned in Linux:

You can use the following command to adust the swappiness on-the-fly:
```
sudo sysctl -w vm.swappiness=10
```
The number can be anything between 0 and 100, 0 means that swap is never used and 100 means that swap is used as much as possible. '10' is a bit low for desktop machine but might be nice for laptops to save power (with less hard disk usage).

I don't think that setting it to zero means that swap is never used - rather that it is never used if cache can be freed up first. I have swappiness set to 0 on my machine (2GB of RAM), and swap still gets used when I'm working with big files.

---

### Post by mcduck on 2008-01-01
> **chrisccoulson said:**
> I don't think that setting it to zero means that swap is never used - rather that it is never used if cache can be freed up first. I have swappiness set to 0 on my machine (2GB of RAM), and swap still gets used when I'm working with big files.

True. But in normal use it' almost always possible to free some RAM by dropping cached data. OF course when handling 4GB files with 1GB of RAM the swap will be used no matter what setting you have for swappiness.

---

### Post by bingoUV on 2008-01-01
A properly coded program would not necessarily allocate 4GB virtual memory to handle a 4GB file. Say you have to search a file for some text. The program should read a block (programmer gets to decide what is a block here, but mostly wouldn't be GBs), search in it and free the memory before reading in the second block. So swap need not be used even if you have 256MB of memory and handle 4GB files.

---

### Post by chrisccoulson on 2008-01-01
Also, just to point out - on my machine (also with 2GB of RAM), I don't notice any performance increase/decrease when I lower the swappiness.

---

### Post by mcduck on 2008-01-02
> **bingoUV said:**
> A properly coded program would not necessarily allocate 4GB virtual memory to handle a 4GB file. Say you have to search a file for some text. The program should read a block (programmer gets to decide what is a block here, but mostly wouldn't be GBs), search in it and free the memory before reading in the second block. So swap need not be used even if you have 256MB of memory and handle 4GB files.

It depends what the program is doing. For text doing it that way is not a problem, for example Sed is a nice streaming editor that can handle as big files as you ever wish, as it only reads one line at a time.

But if you want t o open a 4GB picture, you _need_ to open the whole file at one time. There is no other way. You can't just open the picture one piece at a time, you'd never actually see the whole picture. Same goes for many other types of files people may need to edit on their machines..

So it's not just a question of 'proper coding', but also of what the program does, and if it's even possible to divide the file to smaller chunks for editing.

---

### Post by TidusBlade on 2008-01-03
Woah, didnt check here in some time, Thanks for all the replies guys, some useful information. Ill just adjust the swap to ~25, should be good then. A firefox restart every now and then could help, since it runs sometimes for over 24 hours without closing it, same goes for other programs, so I do a relog every 12 hours or so, and things seem to be fine :)

---

