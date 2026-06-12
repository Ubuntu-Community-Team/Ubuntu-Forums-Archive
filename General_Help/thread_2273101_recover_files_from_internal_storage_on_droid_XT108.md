---
title: "recover files from internal storage on droid XT1080"
date: 2015-04-10
forum: General Help
---

### Post by elj4176 on 2015-04-10
I have a motorola droid Maxx 1080 and was copying the pictures from the internal 32GB storage when ubuntu had a general error and closed the transfer. I unplugged the usb cable and plugged it back in but the internal storage dcim folder was empty. All of my music was also gone. Tried rebooting the phone and laptop - same thing.

So I thought I could just unmount the phone and run something like photorec or recoverjpeg and get the files. Nope. The internal storage doesn't work that way (please tell me how to do it if I'm wrong). Nothing other than sda (ubuntu) shows up in gparted either. 
I do see new devices show up in /dev but I can't scan them with anything to recover the files. I do see the xt1080 show up in thunar and can browse it just fine - but it's empty.

I googled a bit and seems that if I want to root my device and use windows and some sketchy mobile apps I might be able to get my files but I'm not sure that's the only way.

Any help??
Thanks.

---

### Post by Holger_Gehrke on 2015-04-10
On newer Android devices data transfer isn't done by making  (part of) the memory available as an USB storage device but by using MTP - the media transfer protocol. The reason for this is that with a USB storage device Android had to unmount the storage, make it available and remount it after transfer and for this to work, you had to have a fixed split between system and user storage (basically two partitions), which you don't need when doing things the new way. This obviously makes it impossible to do low level operations like file recovery from a connected PC since MTP always works on files and doesn't offer any kind of access to the underlying block device. On Ubuntu the gvfs - Gnome Virtual File System - makes this transfer operation look the same as access to a file system. But since it's actually only a transfer protocol, this makes me wonder why it lost your data when your PC aborted the transfer, unless you were doing a **move** operation and not a copy; then the droid might have seen the abort as "copy is finished, delete the copied files" ...

Long story short: No chance of doing it from the PC; rooting and "sketchy mobile apps" might actually be your only choice.

---

### Post by elj4176 on 2015-04-10
I was afraid of that. Thanks for the explanation.

---

### Post by elj4176 on 2015-04-14
Ok- I'm beginning to think this has something to do with mtp on linux. If I plug my droid into a windows box I can use it fine. My old files are still gone but it works as I would expect. I can create folders and move or copy to/from the droid.

If I plug it into ubuntu (I've tried 2 different ubuntu machines - albeit both are 14.04) it doesn't work right. I can see the droid and can browse the files but I cannot alter the files on it and I cannot copy or move anything onto it. I get an mtp error and there are strange named folders (looks like chinese maybe?). Those same folders under windows are called something like '/storage/emulated/0/' - something like that. I noticed the goofy folder names when I had the initial problem and lost all my files.

---

