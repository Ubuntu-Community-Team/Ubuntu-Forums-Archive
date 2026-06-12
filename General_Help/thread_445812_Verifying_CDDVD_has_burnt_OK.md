---
title: "Verifying CD/DVD has burnt OK?"
date: 2007-05-16
forum: General Help
---

### Post by evolutionx on 2007-05-16
Hi everyone,

Does anyone know an easy way to verify if a CD/DVD has been burnt correctly?  

I recently downloaded a bootable ISO and ran sha1sum to make sure it downloaded OK, which it said it did.  Then I burnt it to disk using GnomeBaker but after rebooting with the new disk in the drive the system would not boot off it.

I have burnt a few other CD's using GnomeBaker with no problems but this is the first time burning a DVD using it.

Thanks in advance.

---

### Post by ayenack on 2007-05-16
The easy way to burn an iso is to right click on the iso image and then choose write to disk from menu this will always burn the iso image correctly dvd/cd/rw does not matter. If you open the dvd iso cd and it looks like this then the image is most likely OK.

_Folders_
dist
doc
install
isolinux
pics
pool
preseed
ubuntu

_Files_
cdromupgrade
md5sum.txt
README.diskdefines

Best of luck. ayenack.

---

### Post by zvacet on 2007-05-16
When you boot up you have option chek CD for errors or something similar.Do it and if any errors are found download same version with torrent and point download at the folder where your iso is.Torrent will chek your iso and replace corrupted files with good ones.So you will not do complete download,just corrupted files.After that burn it at slower possible speed and you should be fine.

---

### Post by ayenack on 2007-05-16
I don't think the DVD is even booting I think it's booting past it into the normal OS so he will not be able to check the DVD if this is the case. He may need to change the boot order in BIOS might have been changed so as not to boot from CD/DVD drive.

ayenack.

---

### Post by evolutionx on 2007-05-17
Hey,

Thanks for the tips.

Yeah the computer boots and gets past the bios, then the CD spins up and comes up with some errors.  I might try another brand of DVD to see if that fixes it.  I can boot the computer off other CD's OK.

Is there any way of using something like md5sum/shasum1 to check the newly burnt CD for errors?

---

### Post by ayenack on 2007-05-18
> Is there any way of using something like md5sum/shasum1 to check the newly burnt CD for errors?

Not that I know of.

As zvacet said you can use the check that is already on the DVD/CD when you put it into your system on boot there's an option to check the disk for errors, can take while to do it though. Can be worth doing but normally I just try the install then if that fails (which is rare) I'll check the DVD/CD to see if it has any errors. If a DVD/CD is bad it normally will not load anyway. A good check to do is file size if the download was 4.1GIG and the DVD has 4.1GIG on it then chances are that it's downloaded so any fault will be with the DVD/CD.

Anyway best of luck with the new install. ayenack.

---

### Post by fede on 2007-05-29
Hello

k3b comes with the option to verify cds / dvds after burning (just like Nero does in windows). It seems to me that it uses md5/sha1 to hash the iso or compilation before burning and then verifies the writen cd against it. I don't really know how it works, but it works; maybe that's a big reason why a lot of people consider it the best burning app.

It uses qt libraries, so if you are running gnome it might require some kde dependencies. There is nothing bad about that IMHO, it will simply use some more space.

Check it out through synaptic or by typing 

```
sudo apt-get install k3b
``` 

in a console. Hope it helps.

---

### Post by zvacet on 2007-05-29
[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

---

