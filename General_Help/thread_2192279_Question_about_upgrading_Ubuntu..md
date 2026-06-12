---
title: "Question about upgrading Ubuntu."
date: 2013-12-07
forum: General Help
---

### Post by mjalberts13 on 2013-12-07
Hi everyone,

If I upgrade to other versions of Ubuntu like 12.10/13.04/13.10 will I  lose all my files? and so will my stubborn wireless dongle's drivers have to be  installed again?

Thank you
MJ

---

### Post by claracc on 2013-12-07
No, your home folder is preserved.

About the wireless, the upgraded software, in the beginning, will control it better, but in order to avoid problems before upgrading you can try the live CD or DVD of the new release.

---

### Post by 3rdalbum on 2013-12-07
> **mjalberts13 said:**
> Hi everyone,

If I upgrade to other versions of Ubuntu like 12.10/13.04/13.10 will I  lose all my files? and so will my stubborn wireless dongle's drivers have to be  installed again?

Thank you
MJ

I had a nice, descriptive reply written out for you... and then my computer crashed (hardware problem - the data cable to the hard disk failed) so I lost it all.

In a nutshell, you shouldn't bother going to 12.10 or 13.04 because they will only be supported for five months or less. 13.10 will be supported for the next eight months, so if you are upgrading, this is what you should upgrade to.

13.10 has newer drivers, so it might have the correct wireless driver already loaded. If it doesn't, though, you will need to reload your wireless driver. You do for any kernel update.

The best way of getting to 13.10 is to download the DVD image, burn it and boot from it, and install 13.10 to the same partitions that you currently use. As long as you don't tick the "Format" box, your files will be preserved. **EVEN** if your /home is on the same partition as /, your personal files and settings on /home will be preserved.

---

### Post by mjalberts13 on 2013-12-07
> **3rdalbum said:**
> I had a nice, descriptive reply written out for you... and then my computer crashed (hardware problem - the data cable to the hard disk failed) so I lost it all.

In a nutshell, you shouldn't bother going to 12.10 or 13.04 because they will only be supported for five months or less. 13.10 will be supported for the next eight months, so if you are upgrading, this is what you should upgrade to.

13.10 has newer drivers, so it might have the correct wireless driver already loaded. If it doesn't, though, you will need to reload your wireless driver. You do for any kernel update.

The best way of getting to 13.10 is to download the DVD image, burn it and boot from it, and install 13.10 to the same partitions that you currently use. As long as you don't tick the "Format" box, your files will be preserved. **EVEN** if your /home is on the same partition as /, your personal files and settings on /home will be preserved.

I have read on some other threads that if you wish to upgrade it is recommended to go from 12.04 to 12.10 to 13.04 to 13.10 is this then untrue? [here]("http://askubuntu.com/questions/322252/upgrading-from-ubuntu-12-04-to-13-10") is the post.

---

### Post by germanix on 2013-12-07
If you wish to "upgrade" this would mean either using the "software manager" or the "terminal" to upgrade to the newest version of the OS, the recommendation would be to upgrade to each individual version step be step as you mention above. My view is it is always better to do a clean install. So I would agree with "3rdalbum" advice to you. Rather just burn a copy of 13.10 if that is were you want to go, and test it on your hardware first in live mode. If all works and you are happy you then install it fresh as already suggested above.

---

### Post by mjalberts13 on 2013-12-07
Thank you very much! :D

---

### Post by Sef on 2013-12-07
If you are using an LTS version and wish to stick with it, then you can upgrade to the next LTS version.  Otherwise, you have to upgrade version by version.

---

