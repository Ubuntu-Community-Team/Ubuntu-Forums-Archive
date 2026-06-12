---
title: "Adept says requested &quot;no change&quot;"
date: 2007-02-08
forum: General Help
---

### Post by Morientes on 2007-02-08
I just tried to download new packages in Kubuntu. It downloaded and installed a lot, but there are three left where it, in adept under Requested, says "no change". What does this mean? The three packages are linux-image-generic 2.6.17.11 and linux-headers-generic and linux-restricted-modules-generic. I do not use a custom kernel or anything. I use the out-of-the-box generic one...

Is something wrong?

---

### Post by mafitzpatrick on 2007-02-08
I've got the same problem here Morientes.  Selecting them manually and choosing to upgrade turns "no change" into a rather offputting "BREAK (upgrade)" in red.  Won't be doing that any time soon.

Anyone know what could be causing this, or how to fix?

Thanks

---

### Post by Morientes on 2007-02-08
Yes exactly, forgot to mention that. I also tried selecting upgrade and it also result in the "break" message...

Anyone know what's wrong?

---

### Post by mafitzpatrick on 2007-02-08
Replying to my own post [this page](http://www.debian-administration.org/articles/69)  appears to give an explanation. The upgrade requires new packages to be installed & so is being blocked.  

If you check the details (e.g. for linux-headers-386, a metapackage) it says it is dependent on linux-headers-2.6.17.11 (the real one).  However, that is greyed out in the list and unavailable.

Looks as though the update of the repository has been incomplete.

---

### Post by Morientes on 2007-02-08
Hm, ok. Any idea how it can be fixed?

---

### Post by brharri1 on 2007-02-08
I am also having this issue: linux-image-386 and linux-restricted-modules-386 request no change, and if I request an upgrade, it says BREAK in red. 

-Brian

---

### Post by Morientes on 2007-02-08
It is correct that it says that they require some other packages. F.ex the linux-image-generic requires the linux-image-generic-2.6.17-11 or something like that.. Should one just apt-get install the packages that they are dependent upon?

---

### Post by lalinux on 2007-02-08
Just for information, I am having the same problem.  I got an update notification this morning which did update some things.  After rebooting I had two more left that won't update without breaking something.

The two I have left are linux-image-386 and linux-restricted-modules-386

---

### Post by Morientes on 2007-02-08
Hm, is it an error with the packages? We seem to be a lot of people having the problem now...

---

### Post by Morientes on 2007-02-09
If I try to install one of the packages that it says they require, I am told that the package is unavailable but is referred to by another package. I think maybe the problem is with our sources.list.
Can anyone confirm this? And maybe supply a clean sources.list that we can try?

---

### Post by lalinux on 2007-02-09
Well as I got up this morning and logged on to my Kubuntu machine, I saw the update notifier was still active.  So I tried again and noticed there were several new packages, and when I ran the update everything went through without a problem.  Some repository person from on high must have heard and fixed it.

case solved!

:)

---

### Post by Morientes on 2007-02-13
And it works for me too, so thats nice! :-)

---

