---
title: "data recovery from swap:confused:"
date: 2007-12-11
forum: General Help
---

### Post by shilpa1 on 2007-12-11
hello geeks,
i am a newbie
i saw this in a FORUM regarding swap ...is this true?
[U]a point to bear in mind is those occasions when the computer is powered down unexpectedly, such as during a power cut.  you can lose data if you don't have a swap partition.

think of swap as a buffer between what is in memory and what is stored on disk.  in order to keep ram as free as possible, the system stores anything not currently in use in swap.  it will also store what you may be typing in kate, the temporary video/audio files you're ripping, the artwork you're slaving over in gimp and so on.

an abrupt powerdown will lose all that data.  if you have a swap partition, most, if not all, of that data is in that partition and recoverable.

if nothing else, swap is a handy failsafe.
[/U]
is this true?
if yes how can i recover data from swap?:confused:

---

### Post by Jimmey on 2007-12-11
Use photorec on the swap partition. Bear in mind that if you start writing to swap again (alot), then the files will probably be overwritten.

```
 sudo apt-get install testdisk && sudo photorec
```

---

### Post by bingoUV on 2007-12-11
Shilpa, the text you quoted is incorrect. Can you mention the source where you found it?

This is not to say stuff cannot be recovered from swap. But data is not at all guaranteed  to be saved in swap partition even if there is a swap partition. Especially if you have enough memory. And if your computer gets accidentally powered off, booting it again might also lose you the data that could have been in swap. So next time if you are booting for data recovery from swap, you have to boot in a way that the swap partition does not get used as swap.   

If you keep this in mind, photorec might help you do that, I have never tried it.

---

### Post by shilpa1 on 2007-12-13
dont remember the exact forum somewhere in net i registered in a lot of forums to learn linux
someone also in a private message gave me this link....
> The kernel can discard a clean page whenever it needs the memory for something else, because it knows it can always get the data back from disk. However, dirty pages need to be saved to disk before they can be reused. We call this eviction. So flushing pages in the background has two purposes: it helps protect data from sudden power cuts, and more importantly it means there are plenty of clean pages that can be reused when a process needs memory.

he/she was using this as referance i was told ....since there was not much to discussion in forum
[http://sourcefrog.net/weblog/software/linux-kernel/swap.html](http://sourcefrog.net/weblog/software/linux-kernel/swap.html)

a person said this in orkut i believe...
> First of all let me make clear that swap doesnot have any kind of JFS or any traditional Unix filesystem. It doesnot have infact a filesystem on it. So forget about fsck program doing crash recovery of swap partition.
Lets say there are appln certain processes running on a system and due to mem pressure Unix kernel has moved the pages of these processes to swap disk partition. They are now being continously being pagedout and pagedin as per the requirement of those processes. Now say system crashes. U reboot the system. Now why in the first place the pagedout data from swapspace needs to be recovered. That's the PAGEDOUT data of binary processes that were running before system crashed. After rebooting they are not running. So what's the use of pagedout data. I mean if process P1 was once running and certain of it's private data was pagedout on swap , then after system has rebooted howcome that pagedout data is imp, boc P1 is not running now.
Crash recovery with JFS filesystems or any other normal Unix filesystems is for maintaining integrity of data. Filesystems deal with DATA. SWAP deals with Pages which actually are not data but parts of running Process images. 


whom to believe ?and who is wrong?i was curious...
because if my system crashes during a memory hungry program and i was doing some program in background which i had not saved will i be able to recover it?
and i wanted a explanation which is middle path not too technical not too simple...what exactly goes on during swapping?about the filesystem stuff i dont know?is that true too?

---

### Post by bingoUV on 2007-12-13
Depends on what you mean by recover. If you want to get data that the program was working on it should be possible. If you know something about the program unsaved data (like some of the contents), you could find the known data in the swap partition, and thus find out the surrounding stuff you did not know about. As I mentioned earlier, all data need not even be present in the swap partition, so it may not be worth all this trouble. 


But if you want the program to run again as if it was never interrupted, it is not possible without serious hacking. Even after serious hacking, it is impossible if some of the required data is not available in swap partition as is very likely.

---

### Post by shilpa1 on 2007-12-14
> If you want to get data that the program was working on it should be possible. If you know something about the program unsaved data (like some of the contents), you could find the known data in the swap partition, and thus find out the surrounding stuff you did not know about.

yes i want to know say if i am working on openoffice impress and a dvd ripping program and a video player and something else that i was watching video for a long time and impress i was in middle not saved  got bored and was running in background.

suppose system crashes and impress was using swap...(.will it be using swap if my memory cud not keep up?dont know )

i know what i was creating in impress and want to recover it from swap .....
will this be possible...(dont say office itself has recovery..)..suppose some other program ....and was using  swap ....now can i get data back in impress or the program i was working in background if system crashes?i would know what i was typing /creating 

if yes can photorec do this?
if yes was curious.....what exactly goes on in background?
> But if you want the program to run again as if it was never interrupted, it is not possible without serious hacking.
is it possible?to rerun program as if it was never interrupted?vaw that would be good

---

