---
title: "Solid State Drive SSD Write Minimisation"
date: 2008-05-24
forum: General Help
---

### Post by drsox1899 on 2008-05-24
I just lashed out and bought a Mtron 16GB SSD 100+ MB/s read and 80+ MB/s write.  Hey, why not !

But I need to minimise the write frequency on this drive as that is the bugbear of these Flash based SSDs.  Here's what I plan to do - comments welcomed.

I am fortunate to have another fast drive - a WD 10k RPM Raptor. So I am going to put the /home partition and the swap partition on this drive (74GB).

If I put the / partition on the SSD then there should be minimal writes ? Yes ?

I also am dual booting with WinXp, so I shall put the C:/ drive on the SSD and disable Virtual Memory and Paging as per this link : [http://www.addonics.com/support/faqs/faq-bootcf.asp](http://www.addonics.com/support/faqs/faq-bootcf.asp).

All the data drives will be on the WD Raptor.

If I can slim down the WinXp partition to 5-6GB, how much should I expect to use for Ubuntu 8.04   / partition (remember /home is on another drive) ?

Thanks

---

### Post by shae on 2008-05-24
Yes and no.  Most of the root file system is rarely written to.  There are two exceptions though.  /tmp and /var  You should put these on your data drive also.

Usually 8-10 GB is safe for the root partition as long as you install large games in your home folder.

---

### Post by nsche on 2008-05-24
I think you want to disable access recording.  I think the mount option is noatime

---

### Post by sdennie on 2008-05-24
You may also want to avoid using a journaled filesystem as that will increase the number or writes that happen to the disk when writes are done.  Or, better yet, I believe it's possible to store the journal on a separate disk though, I've never done this and it might be overkill.

---

### Post by drsox1899 on 2008-05-25
Thanks for the info.

Will Ubuntu install with no Swap file ?

If I use the ext2 then this is not a journaling system ?

If I put /tmp and /var on my other drive am I not just averaging the system response time between the two drives ?  
Does anyone have a feel for the trade-off between reducing drive writes on the SSD and increasing system response time by making the system access both drives ?

noatime I will look into.  Googling it gives a link to an Ubuntu thread : [http://ubuntuforums.org/showthread.php?t=107856&page=2](http://ubuntuforums.org/showthread.php?t=107856&page=2). 
This refers to reiserfs as well as ext3, but not ext2.

There's also this impenetrable reference link to Embedded Flash Linux : [http://www.ssiembedded.com/embedded_linux_managing_memory.html](http://www.ssiembedded.com/embedded_linux_managing_memory.html).  I'll try to work my way through it !

The relevant piece in this link is this : "" The &#8216;noatime&#8217; option turns off the updating of file access times, which would cause a flash write every time a file is read.  ""  

nsche - is this what you mean ?   What about relatime instead of noatime ?  See this link : [http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/)

Fortunately there is already some forum traffic on this subject in the Asus EEE forums as this has a Flash Drive.  
The Linux though is Xandros (I'm a convert from Xandros to Ubuntu) See : [http://forum.eeeuser.com/viewtopic.php?id=890](http://forum.eeeuser.com/viewtopic.php?id=890)

---

### Post by h4mx0r on 2008-05-25
add noatime and nodiratime to /etc/fstab and don't use a swap partition. Windows usually eats through even regular drives we've been through 3 almost and only been a few years with living room pc here.

---

### Post by sdennie on 2008-05-25
ext2 will certainly cause fewer writes than ext3 (as you guessed, it's not a journaled filesystem) but, as I said, it might be overkill for a mostly read-only filesystem.  I believe noatime should work fine on ext2.

Putting /tmp and /var on a non-SSD disk is a good idea and you almost certainly won't notice any performance decrease by doing so.

---

### Post by drsox1899 on 2008-05-25
Fortunately I have a test PC for trying out this.

What would be a good size for /tmp and /var - 2GB each ?

Can I have ext2 for /  and ext3 for /tmp, /var and /home or is this going to be a problem ?

I have to have a swap file it seems with U8.04.

I'll try this out before using the SSD

---

### Post by drsox1899 on 2008-05-26
> **h4mx0r said:**
> add noatime and nodiratime to /etc/fstab and don't use a swap partition. Windows usually eats through even regular drives we've been through 3 almost and only been a few years with living room pc here.

I've seen in some Linux forum posts that noatime is a superset of nodiratime and that specifying the former will also achieve the latter.  Correct ?

---

### Post by nsche on 2008-05-26
> **drsox1899 said:**
> ...
The relevant piece in this link is this : "" The ‘noatime’ option turns off the updating of file access times, which would cause a flash write every time a file is read.  ""  

nsche - is this what you mean ?   What about relatime instead of noatime ?  See this link : [http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/)

Fortunately there is already some forum traffic on this subject in the Asus EEE forums as this has a Flash Drive.  
The Linux though is Xandros (I'm a convert from Xandros to Ubuntu) See : [http://forum.eeeuser.com/viewtopic.php?id=890](http://forum.eeeuser.com/viewtopic.php?id=890)

That is exactly what I was referring to.  The Linux distribution will not matter.  What we are speaking of is characteristics of the kernal and the file systems.  It is possible some dist may have a version of mount that did not support some option but the version of the kernal is the important part.

In regard to use of ext2 or ext3 for /tmp... Ext2 and ext3 are basicly the same with the addition of journaling in ext3.  Why would you want journaling for a temp system.  You probably will not be able to reuse the files if you had a crash so the capability to recover the files that you get from journaling would be of little value but it would have some cost.  You could even look at using a ram file system for /tmp.  Solaris used that for a long time (I am not sure if they still do that).

---

