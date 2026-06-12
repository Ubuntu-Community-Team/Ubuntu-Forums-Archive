---
title: "Do I really need a swap partition?"
date: 2008-05-29
forum: General Help
---

### Post by the lemming on 2008-05-29
I've been away from Linux for a while and now that I have built my first PC the spec seems to like the Ubuntu live CD.  This may seem like a silly question but do I need a Swap file?

Cheers

---

### Post by george9233 on 2008-05-29
I think swap partition is not that neccessary if you have more than 1 GB ram, unless you use programs that use huge ram such as virtualization softwares. I use Sun xVM Virtualbox to try out different linux distros. Only during these times the ram usage can go up to 1.5 GB of my 2 GM ram, but the 3 GB swap was only used by about 300 MB. In normal daily operations the ram usage usually never exceeds 1 GB.

---

### Post by the lemming on 2008-05-29
So if I do have a Swap file do I stick the the two and a half times the size of my RAM formula?

My laptop has 1.2gb of RAM giving the potential of 3gb swap

My desktop has 2gb of RAM giving the potential of 5gb of Swap

Are these sizes normal or way too large given that you hinted that you seldom dip into your Swap File?

Cheers

---

### Post by jimbob on 2008-05-29
You should have a swap partition at least as large as your total ram size.

I have experienced systems that become slow and sluggish for no apparent reason and discovered that there was no swap space assigned.

If you are running any of the virtualization software you definitely need it.

---

### Post by FuturePilot on 2008-05-29
If you want to hibernate the computer then yes you will need swap for that. If you do heavy multi tasking or lots of multimedia stuff, then you will want a swap partition. 

If you go with all the defaults in the Ubuntu installer, it will automatically create a swap partition the appropriate size.

---

### Post by Dr Small on 2008-05-29
I have 1GB of RAM and 256MBs of Swap. Why? Because I rarely use more that 250MBs of my RAM. I run minimalistic anyhow...

---

### Post by the lemming on 2008-05-29
> **FuturePilot said:**
> If you want to hibernate the computer then yes you will need swap for that. If you do heavy multi tasking or lots of multimedia stuff, then you will want a swap partition. 

If you go with all the defaults in the Ubuntu installer, it will automatically create a swap partition the appropriate size.

That's interesting to know about media work as I am trying to convert my DVD collection to MP4 (H264)

Would a 5gb Swap file be too large?

My laptop has an 80gb drive and I haven't decided to dual boot with XP or do a fresh install of Ubuntu only.

My desktop has several hard drives but I only keep the Vista OS on a 80gb drive with nothing else on that drive.  That system would definitely be a dual boot so with this in mind how big would I make the Swap partition and the / partition?

---

### Post by george9233 on 2008-05-29
> 
So if I do have a Swap file do I stick the the two and a half times the size of my RAM formula?

My laptop has 1.2gb of RAM giving the potential of 3gb swap

My desktop has 2gb of RAM giving the potential of 5gb of Swap

Are these sizes normal or way too large given that you hinted that you seldom dip into your Swap File?

Cheers


I think that's a little bit too large, but if you have enough free hardrive space it won't be problem to assign more swap sapce. And while using the system you can find out how much swap space is actually used. It would be a good experience for future installations.

---

### Post by danwood76 on 2008-05-29
Your swap should be at least the size of your RAM, if you have 1GB or more.
Or if you have less than a gig then make it double your ram.

So I have 2GB of RAM and a 2GB swap, this allows for full hibernation, I do a load of video encoding/transcoding and sometimes use as much as 50MB of my swap (I know its a lot ;))

Anything greater than your RAM size (with at least a gig of ram) is just wastage as you rarely use much swap but you will possibly need the whole amount if you hibernate.

---

### Post by bodhi.zazen on 2008-05-29
In general SWAP is used as RAM on your hard drive. But, the formula swap = ram x2 is outdated.

In general I use SWAP = RAM x 2 ; max 1 Gb or if you use hibernation of suspend SWAP = RAM

Here are some links on memory and swap :

[http://ubuntuforums.org/showthread.php?&t=327496](http://ubuntuforums.org/showthread.php?&t=327496)

[http://www.linux.com/guides/sag/swap-allocation.shtml](http://www.linux.com/guides/sag/swap-allocation.shtml)

[http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html](http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html)

[http://lwn.net/Articles/83588/](http://lwn.net/Articles/83588/)

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?)

---

### Post by timcredible on 2008-05-29
yes, you need a swap partition (not a swap file, that's what windows does).  your system will have issues if it needs swap and there isn't any.  unless you're short of hard drive space, go ahead and use 1gb or 2gb for swap.

---

### Post by bodhi.zazen on 2008-05-29
> **timcredible said:**
> yes, you need a swap partition (not a swap file, that's what windows does).  your system will have issues if it needs swap and there isn't any.  unless you're short of hard drive space, go ahead and use 1gb or 2gb for swap.

You can use a swap file on Linux as well as a swap partition.

[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

---

### Post by Quillz on 2012-01-27
I'm presently installing Ubuntu onto my ThinkPad without a swap partition. Will I be able to add one later, and if so, how?

The reason I didn't add one now was because I'm attempting a dual-boot with Windows 7, and was afraid using my NTFS partition (which has Win7) as a swap partition would make Windows unbootable. Is this the case, or is it fine to assign my NTFS partition as Ubuntu's swap partition? (If I'm able to go back later and add one, that is.)

---

### Post by danwood76 on 2012-01-27
Yes, you should not use your windows partition as a swap.
To use it as a swap it will have to reformat and delete all your data.

For the system to run smoothly swap is recommended. In windows you don't have a choice about it (the pagefile is used in a similar vein to swap).

The best option is to reduce the NTFS partition size and create the swap, it only requires to be the same size as your RAM so it wont use much hard disk space.

The Ubuntu installer should offer you this option anyway though.

---

### Post by Quillz on 2012-01-27
> **danwood76 said:**
> Yes, you should not use your windows partition as a swap.
To use it as a swap it will have to reformat and delete all your data.

For the system to run smoothly swap is recommended. In windows you don't have a choice about it (the pagefile is used in a similar vein to swap).

The best option is to reduce the NTFS partition size and create the swap, it only requires to be the same size as your RAM so it wont use much hard disk space.

The Ubuntu installer should offer you this option anyway though.
Ah, glad I didn't do anything, then. I guess I'll use GParted or some other in-OS tool to make another partition, then.

Thanks for the info.

---

### Post by oldos2er on 2012-01-27
Since your issue seems resolved I'm closing this four year old thread. Next time please start a new thread for your question or problem.

---

