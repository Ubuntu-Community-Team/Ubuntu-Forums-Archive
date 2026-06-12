---
title: "Another kernel inquiry"
date: 2012-10-17
forum: General Help
---

### Post by Deucalion29710 on 2012-10-17
If I was to get the latest stable kernel (3.6.2) from here:  [http://www.kernel.org/](http://www.kernel.org/)  and the patch, how do I install it?  Does it simply have the 4 deb files within the compressed file?

---

### Post by pqwoerituytrueiwoq on 2012-10-17
the mainline one?
i have made some scripts for this:
[http://ubuntuforums.org/showthread.php?t=2071903](http://ubuntuforums.org/showthread.php?t=2071903)
if you are running 12.04 i read 3.6.2 did not work on it
3.6.2 works just fine for me on 12.10
the update checker only offers ones for your release so 3.6.2 is only offered to 12.10
but the 3.6.2 installer will install 3.6.2 on 12.04 but there is no guarantee the kernel will work for you

---

### Post by Deucalion29710 on 2012-10-17
I am running 12.04.  My current kernel is 3.5.4, which is not even listed there.  I still have some hiccups with my connectivity.  Any idea what would work for me?

---

### Post by pqwoerituytrueiwoq on 2012-10-17
i don't know how you are connected...

---

### Post by Deucalion29710 on 2012-10-17
It's connected via Android USB tethering.  It drops the connection sometimes and does not even notify me that is has gone offline.  I have a good signal and I am still able to navigate on the phone.  Win7 was able to keep connected as long as I needed to be.  Another issue that I am having is that my USB hard drive usually does not mount on boot.  I have to unplug it and plug it back in to make it come up.

---

### Post by oldos2er on 2012-10-18
You might want to start a new thread in the Networking & Wireless forum. If you do please be sure to give full details of your hardware and connection type.

---

### Post by Deucalion29710 on 2012-10-19
OK I have a thread in the appropriate place now.  Thanks.

---

### Post by dino99 on 2012-10-19
> **Deucalion29710 said:**
> If I was to get the latest stable kernel (3.6.2) from here:  [http://www.kernel.org/](http://www.kernel.org/)  and the patch, how do I install it?  Does it simply have the 4 deb files within the compressed file?

choose the kernel:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Download the 4 required packages inside an empty folder, then from there:

sudo dpkg -i *

---

