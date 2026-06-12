---
title: "Boot folder size"
date: 2015-06-13
forum: General Help
---

### Post by RogerDavis on 2015-06-13
How can I increase the size of the Boot partition?

---

### Post by dino99 on 2015-06-13
sudo apt-get autoremove

---

### Post by monkeybrain20122 on 2015-06-13
Do you mean a /boot partition? Why do you need one in the first place?

---

### Post by Bucky Ball on 2015-06-13
Scant detail. The answer to your question is boot from live media, launch gparted, resize the boot partition. That's about it with the information you have provided and that is presuming you mean boot partition and not folder. :)

If you want to kill the unused kernels in your boot partition the easy way is to check which kernel you're using with 'uname -a', install and launch Synaptic Package Manager, search for 'linux image', click the 'Installed' column a couple of times, mark to completely remove all but the current kernel number and the one before it. BE CAREFUL here and ask if in any doubt (with a full explanation of where you're at and what you're doing and attach screenshots/code if necessary). 

To improve your chances of getting support now and in future please read the third link in my signature. Take note of point #2. [For instance]("https://duckduckgo.com/?q=increase+boot+partition+size+ubuntu&ia=qa"). Research, if you still can't get it working or you have questions, post. Thanks.

---

### Post by RogerDavis on 2015-06-13
I do mean boot partition. Now corrected.

I had heard in another question that "sudo apt-get autoremove" wouldn't fully clean all the cruft involved with the old kernels.  The info I got was to use Synaptic, details as BuckyBall lays out, complete removal.  Thoughts on that?  As in : where does "sudo apt-get autoremove" fall short?

In any case, the boot partition on that old laptop is very small, I'm just looking to get a bit of extra room.  From what I understand, I don't HAVE to have a boot partition, but it's recommended, and if I remember right, it was automatic when I installed Ubuntu on it.  Key point I learned is to use live disk to boot.

---

### Post by Bucky Ball on 2015-06-13
[Here's one]("http://ubuntuforums.org/showthread.php?t=996053") from 2008. Autoremove still does the same thing ...

From the man pages:

> autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for other packages and are now no
           longer needed.

Autoremove removes the kernels that are no longer used, but it is kind of odd. For me, it only ever offers to remove the last kernel when a new one is installed. That is a bad thing and not sure why this has been implemented. I always keep the newest kernel and the last working one before it in case something breaks in the new one. I can't see the logic in autoremove autoremoving the last working kernel. :-k

Again, oddly, it doesn't offer to remove ALL old kernels. Just seems to be the last one.

---

### Post by v3.xx on 2015-06-13
> **Bucky Ball said:**
> Again, oddly, it doesn't offer to remove ALL old kernels. Just seems to be the last one.
I have seen this around the forum.
```
sudo apt-get autoremove --purge
```
To remove all old kernels.

This does not work for me, but maybe its a version thing.

And like you, I do not like it when a previous kernel shows up for autoremove and I have to lock it to keep it :(

---

### Post by vasa1 on 2015-06-13
Related link?
[http://ubuntuforums.org/showthread.php?t=2240697&p=13251536#post13251536](http://ubuntuforums.org/showthread.php?t=2240697&p=13251536#post13251536)

---

