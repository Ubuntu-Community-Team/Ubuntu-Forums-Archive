---
title: "Mounting a UnionFS system over /system to enable write access to a SquashFS system?"
date: 2014-12-07
forum: General Help
---

### Post by VpNKBQLjz0 on 2014-12-07
I have no idea if I am in way over my head but I really want help on doing this.

Basically I want to root my device ["Telstra T-Hub 2"]("http://www.gadgetguy.com.au/cms/wp-content/uploads/telstra-t-hub-2-preview-06.jpg") <-- Click for image.

However, and this is the hard part. The system partition is apparently a [**SquashFS file-system**]("https://en.wikipedia.org/wiki/SquashFS") (apparently much like a Linux LiveCD) which is apparently 99% [[RO]]("https://www.google.com.au/search?q=read+only")

Now, [apparently in this post]("http://forum.xda-developers.com/showpost.php?p=44686049&postcount=10") (which is the only one of its kind on the entire internet) this person says exactly:

> Option 3 is by far the best option. UnionFS provides a transperent Read-Write  layer for SquashFS filesystems, writing the updates that couldn't be  written to a RO system like squash to another partition (e.g., Ext4 on  SD card). Mount a UnionFS system over /system to enable write access to  the system

*Unfortunately that user on the XDA forums also has never come back to  the forums, and only posted once. So basically it's all I have go to on.* However you can read more of his post in the above link.

So my question is. How exactly do I do this? I have an 8GB SD card and I am quite experienced in using "ADB" and rooting/unrooting and flashing custom firmwares and all sorts of similar tasks on Android devices. (I've owned 7 Android phones)
But I am a little stumped when it comes to super specific stuff like this.

Could someone please help me understand how I can do this?
I am using **Ubuntu 14.04.1 LTS** currently. I know quite a bit about using Ubuntu but well, I have never done anything like this before.

If anyone can actually help me out properly, I would be happy to* buy you a coffee*. I really want this thing rooted and properly usable for my parents (as an early Christmas present) before I have to go back overseas.
This means either by way of asking my any questions at all, (as I would be more than happy to answer them) or providing any sort of tips, or even explaining in detail what I probably have to do.

All the information between the links I've posted should be there. I'm just having a really hard time figuring out mostly where to start. 

P.S. [I've tried a lot of rooting methods, and I mean a lot.]("http://forum.xda-developers.com/general/rooting-roms/how-root-telstra-t-hub-2-ics-download-t2964883") I don't think any of the traditional ones will work because there's pretty much no way to get Read-Write access for the system partition. Which is why I need help on using UnionFS.

P.P.S. Feel free to move the thread if it shouldn't be here. *And I checked with the rules, _discussing rooting is not illegal, nor against the forum rules :)_*

---

### Post by VpNKBQLjz0 on 2015-01-04
I'm going to bump this because I am still actively searching for a way to do this. It apparently has been done before:

[http://forum.xda-developers.com/showpost.php?p=44686049&postcount=10](http://forum.xda-developers.com/showpost.php?p=44686049&postcount=10)

I just need a bit of help in understanding step-by-step how this was accomplished.

---

