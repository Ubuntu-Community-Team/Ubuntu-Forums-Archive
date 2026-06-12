---
title: "Ubuntu 8.04 Live CD"
date: 2008-04-08
forum: General Help
---

### Post by penguin5 on 2008-04-08
I have a dual boot vista and ubuntu 7.10 on my laptop. I tried running a live ubuntu 8.04 beta live cd but it keeps giving me the dual boot menu. I changed the priority boot to CD ( like i did before i got ubuntu 7.04 and it worked fine) but it keeps not recognizing it. How do i run the live CD?

Thanks in advance

-Alex

---

### Post by ibutho on 2008-04-08
You could have a corrupt disc, so check whether the md5sums for your iso matches the ones on the Ubuntu download servers. If the md5sums don't match, download the isos again, preferably using a download manager. If the md5sums match, then burn the iso to disc at a slow speed and see if that makes a difference.

---

### Post by penguin5 on 2008-04-08
> **ibutho said:**
> You could have a corrupt disc, so check whether the md5sums for your iso matches the ones on the Ubuntu download servers. If the md5sums don't match, download the isos again, preferably using a download manager. If the md5sums match, then burn the iso to disc at a slow speed and see if that makes a difference.

Im sorry but I dont understand how to do that. Whats md5 and and where do i go to see if it matches up? 

Sorry for the dumb question.

---

### Post by ramjet_1953 on 2008-04-08
Also, did you burn the image as an iso disk, not an ordinary data disk?

You also need to burn iso's fairly slowly to ensure that you don't have any errors. $ X or the slowest that your burner allows is a good idea.

Regards,
Roger :cool:

---

### Post by FuturePilot on 2008-04-08
It sounds like you may have accidentally burned the CD as a file rather than an image.

---

### Post by penguin5 on 2008-04-08
I extracted the files into a folder and then burned those files from the folder onto the CD. Is that wrong?

---

### Post by ibutho on 2008-04-08
> **penguin5 said:**
> Im sorry but I dont understand how to do that. Whats md5 and and where do i go to see if it matches up? 

Sorry for the dumb question.
md5sums are a checksum. Your iso has a checksum to ensure its integrity, which can be checked by running
```
md5sum somefile.iso
```
The checksum will be printed on the screen and you can compare it with the ones on the Ubuntu servers. You can also find the checksums for 8.04 on this [site]("http://releases.ubuntu.com/releases/8.04/"). Look at the file named MD5SUMS.

---

### Post by Therion on 2008-04-08
See the how-to: [Burning an .iso](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by penguin5 on 2008-04-08
> **ibutho said:**
> md5sums are a checksum. Your iso has a checksum to ensure its integrity, which can be checked by running
```
md5sum somefile.iso
```
The checksum will be printed on the screen and you can compare it with the ones on the Ubuntu servers. You can also find the checksums for 8.04 on this [site]("http://releases.ubuntu.com/releases/8.04/"). Look at the file named MD5SUMS.

I tried running the checksum but got this : No such file or directory. How do i check the file?

Thanks for your help

---

### Post by ibutho on 2008-04-08
It seems like you entered the wrong file name. You need to replace somefile.iso with the exact path name for the iso that you downloaded e.g.
```
md5sum downloads/iso/ubuntu-7.10-desktop-i386.iso
```
Another option is to change into the directory you downloaded the iso and then run md5sum e.g.
```
cd downloads/iso
md5sum ubuntu-7.10-desktop-i386.iso

```
Anyway having looked at one of your posts above (I think I missed it earlier), it seems like your burnt the disc wrongly. You were not supposed to extract the contents of the iso. Instead, you were supposed to burn the iso to a cd as a "cd image".

---

### Post by penguin5 on 2008-04-08
thanks, i got it to work.

---

