---
title: "disk made loud noise while loading flash, now stuck at initramfs during boot"
date: 2012-12-27
forum: General Help
---

### Post by DisorderlyCitizen on 2012-12-27
hi guys,

as the title states, while watching a youtube video, my disk made a very loud, very fast clicking sound. i still heard sound but my laptop froze so i did a hard reset. since then, everytime i boot up my laptop, i get stuck at a prompt which says (initramfs). i am running lubuntu 12.10.

some things that i noticed:

during boot up, i get a grub menu. this wasnt the case before as i only have 1 os installed.

when i ls at the (initramfs) prompt, i see an incomplete file structure. /home is missing, for example.

i got a file at my / named init. i cat'ed this file and at the bottom it says:
panic "Could not execute run-init." 
i do not know if this has something to do with me trying a recovery option from grub, which went without success btw.

also, most of the directories within / are empty. /var is one of them, so i had no luck with finding logs that can tell me more about what happened.

so basically i am out of answers. i am concerned that my hdd died when it made that loud noise.

---

### Post by dabl on 2012-12-27
I'm going to suggest that there is no relationship between what software was running, and the sound made by the hdd.  Putting it another way, SOMETHING will be running when every hard drive in the world eventually crashes.

Better boot a Live CD, and see if there is any ability to back up data on that hard drive.

---

### Post by RedRat on 2012-12-27
It sounds as if your HD is toast. You can try using the live CD to look at your old HD, perhaps you will be lucky and can recover some portion of it. Luckily, HDs today are relatively inexpensive so you get to do  virgin install of Ubuntu on the new disk.

---

### Post by DisorderlyCitizen on 2012-12-27
luckily i had nothing important on my laptop, but i will try to boot off a livecd tomorrow, i'm too tired now.

correct me if i'm wrong here, but if the disk was broken, wouldn't busybox stop working too? i mean busybox is installed on disk, since unix commands still work i suppose that the prompt can access its contents...

---

### Post by RedRat on 2012-12-27
> **DisorderlyCitizen said:**
> luckily i had nothing important on my laptop, but i will try to boot off a livecd tomorrow, i'm too tired now.

correct me if i'm wrong here, but if the disk was broken, wouldn't busybox stop working too? i mean busybox is installed on disk, since unix commands still work i suppose that the prompt can access its contents...
What you probably heard was the read/write head thrashing about. It may have nicked only portions of the HD, i.e., the portions that control most of the GUI. I think you might want to invest in a new HD. Maybe the next time it will thrash a bit more and pretty much take out the rest.

---

### Post by DisorderlyCitizen on 2012-12-28
ok i have removed the hdd from my laptop and put it into a windows machine. it seems to be working, i have formatted it as ntfs and currently i am doing some routine checks to see the extend of the damage.

on a sidenote, is it possible to boot a vm off an entire hdd? i have just used images before but could i install linux from a vm onto the laptop hdd?

---

### Post by dabl on 2012-12-28
> **DisorderlyCitizen said:**
> 

on a sidenote, is it possible to boot a vm off an entire hdd? i have just used images before but could i install linux from a vm onto the laptop hdd?

I'm confused by your question -- you don't "boot" a VM, you "run" it, using a virtualizing package such as VMware or VirtualBox.

You could, in theory, use a Linux VM to run an installer and install that same distribution on a connected (via USB) hdd or sdhc card or USB stick, but that sounds like the hard way under normal circumstances.  I don't see anything easier than booting a Live CD or USB stick, and using that to install on the hard drive.

---

### Post by DisorderlyCitizen on 2012-12-28
sorry, then i meant running a vm:-P

i wanted to take this approach so i can use a linux image as currently i have no empty usb disk or emtpy cd/dvd. this way i could install linux from an image directly to the hdd. the reason for my question is drivers, i do not know if linux will work on my laptop when i install it via a vm.

---

### Post by Luigi2012SM64DS on 2012-12-28
I believe with VMware you can use your physical disk in a VM.

---

### Post by RedRat on 2012-12-28
> **DisorderlyCitizen said:**
> ok i have removed the hdd from my laptop and put it into a windows machine. it seems to be working, i have formatted it as ntfs and currently i am doing some routine checks to see the extend of the damage.

on a sidenote, is it possible to boot a vm off an entire hdd? i have just used images before but could i install linux from a vm onto the laptop hdd?
You can check the HD for defects using chkdsk in Windows, but I certainly would not trust that disk for anything important. HDs are not supposed to make those kinds of noises, it signals a hardware problem, e.g., a bearing or worn spindle. Be prepared for replacing it in the near future.

---

### Post by dabl on 2012-12-28
> **DisorderlyCitizen said:**
> sorry, then i meant running a vm:-P

i wanted to take this approach so i can use a linux image as currently i have no empty usb disk or emtpy cd/dvd. this way i could install linux from an image directly to the hdd. the reason for my question is drivers, i do not know if linux will work on my laptop when i install it via a vm.

OK. Yes, there is a potential issue with the drivers -- the VM will only have the needed driver modules running for the virtualized hardware environment -- they're not likely to be correct for the target (non-virtualized) hardware, even if it is the same computer.

So, you have a running Windows machine, and you have formatted the suspect hdd to ntfs and run chkdsk on it?  One thing you could do is to use unetbootin to install a downloaded ISO image to the connected hdd.  It's a very sub-optimal way to use an hdd, basically you're only going to use 2G or so of it, but if it works it will result in a bootable Linux OS on that hdd.  No ability to save anything, as far as I can imagine -- possibly you could partition it and use the second partition for storage.  I haven't tried that, so no guarantees, and of course that hdd has already shown suspicious behavior ....

---

### Post by DisorderlyCitizen on 2012-12-28
i dont use my laptop for anything important, mostly just for tinkering a little with linux or watching stuff, so that wouldn't be a problem.

i remembered something, a few months ago i tried installing backtrack but couldn't. the installer kept saying that my disk is damaged. however, when i tried installing lubuntu it worked without any errors. could this have been a forewarning of what happened now? why didnt lubuntu write any error message while backtrack did?

---

### Post by dabl on 2012-12-28
> **DisorderlyCitizen said:**
>  could this have been a forewarning of what happened now? why didnt lubuntu write any error message while backtrack did?

Hard to answer "why" something didn't happen some time in the past -- maybe bt uses a media-checking utility that *buntu does not, prior to installing.

The only real way to determine the condition of that hdd is to run the kind of diagnostics that are found on a [**[color=green]hirens boot cd[/color]**](http://www.hiren.info/pages/bootcd) or something like that.  Probably it has some bad sectors, and the way they tend to die is a slow deterioration of the media such that more and more sectors become unreadable as time goes by.  Whatever data or parts of software packages are on the unreadable sectors become errors when you or the system tries to access it.

Although, at the current price of hard drives, I personally find it difficult to justify spending time this way.  My needs for suspected bad media are very few and far between ...

---

### Post by DisorderlyCitizen on 2012-12-29
yes but i am currently going to school, supporting myself. so finances are what you'd barely enough to get by. but i will definitely replace it when i got the means to.

well thanks for alle the help guys

---

