---
title: "Software to entirely defrag a FAT32 hard disc?"
date: 2016-03-26
forum: General Help
---

### Post by gojira2016 on 2016-03-26
I have an external USB hard disc in FAT32 format with some data on it.

I need to entirely defragment it.

(The hard disc will be read by a Playstation 2 with Open PS2 Loader on it. I only mention this to make clear that this hard disc needs to stay in FAT32 format, I am not interesting in changing the file system on that particular hard disc).

While I was still on Windows, I was using PowerDefragmenter for this purpose. The "normal" Windows defragmentation process, i.e. the defrag tool build into Windows, was not sufficient for this.

However I do not have Windows anymore, I only use Xubuntu 14.04, running in a VirtualBox under Mac OS X El Capitan.

Is there something that provides the functionality of PowerDefragmenter and similar software under Xubuntu? What program do you recommend? Can also be command line only, I am fine with that.

TL;DR: What software can I use to entirely defrag a FAT32 hard disc (for use with OPL on a PS2) using Xubuntu 14.04?

---

### Post by sudodus on 2016-03-26
Will you be using any of the files that are stored in the drive? In that case I suggest that you back them up to somewhere else.

After that you can create a new file system. You need not remove the current partition, only create a new FAT32 file system. It will be fresh and empty, and you need not spend time to defragment it.

But if your previous problems depend of hardware problems, that there are bad sectors on the drive surface, it will not help you. Nothing but marking those sectors bad and letting the file system avoid them would help.

I think the best way to check and fix those things is to use ```
chkdsk /r X:
``` where X: is the drive letter, in a Windows system.

It might also work in linux, if you use ```
dosfsck
```. See the manual ```
man dosfsck
``` for details.

See this link for more details: [Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

### Post by gojira2016 on 2016-03-26
Thank you I understand. I have freshly formatted the drive. Then I copy one file on it. When I try to load this file on my Playstation 2 via Open PS2 Loader, I get the error message "game is fragmented". I know this error, apparently there are different types of defragmentation, this error from my experience does not go away when using the on-board Windows defragmentation tools. However it does get away when using tools like PowerDefragmenter. But PowerDefragmenter is only available for Windows.

---

### Post by stalkingwolf on 2016-03-26
have you tried any of the tools on the hirens disk?

---

