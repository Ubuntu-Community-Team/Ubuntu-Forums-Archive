---
title: "replacing /sbin/init"
date: 2014-02-10
forum: General Help
---

### Post by REMIX8604 on 2014-02-10
How common is it to find a rootkit on my ubuntu system? How would it have gotten there? Is it more likely that some one with acess to my machine put it there via the same network?

---

### Post by deadflowr on 2014-02-10
Firstly, which one is it?
What tool did you use to find it?

And as far as someone else using your computer, that'll be one way of getting infected.

---

### Post by REMIX8604 on 2014-02-10
I used chkrootkit and rthunter. I think it found something called "suckit rootkit"

---

### Post by REMIX8604 on 2014-02-10
oh sorry and the infected file was /sbin/init
also 2 java files were marked suspicious. 

I delete the java files... then the /sbin/init.. im sure just by reading this you know my ubuntu wont start anymore. 
how do I get a new /sbin/init file?

---

### Post by bashiergui on 2014-02-10
You need to post more details for anyone to be able to answer your question.


I've been haunting various Linux forums for several years and I can't remember anyone actually finding a rootkit. There have been tons of false positives though. 


Compare your output to these, see if it's the same: [http://ubuntuforums.org/showthread.php?t=1554553](http://ubuntuforums.org/showthread.php?t=1554553)
[https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566](https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566)

---

### Post by bashiergui on 2014-02-10
We posted nearly simultaneously. Research the possibility that it's a false positive (using the links in my previous post) before you replace the file.

---

### Post by Elfy on 2014-02-10
> **bashiergui said:**
> We posted nearly simultaneously. Research the possibility that it's a false positive (using the links in my previous post) _before you replace the file_.

> **REMIX8604 said:**
> ...

I delete the java files... then the /sbin/init.. im sure just by reading this you know my ubuntu wont start anymore. 
_how do I get a new /sbin/init file_?

Too late ...

---

### Post by bashiergui on 2014-02-10
:(

Ugh. I think this has turned into a General Support problem now. But does it boot to grub? Start reading this [https://help.ubuntu.com/12.10/installation-guide/i386/rescue.html](https://help.ubuntu.com/12.10/installation-guide/i386/rescue.html)

---

### Post by Elfy on 2014-02-10
*Thread moved to **General Help**.*

Retitled - you've got bigger issues now than a false positive.

---

### Post by REMIX8604 on 2014-02-10
ok so I got it to boot once again. I made a live usb and copied the init file used on the USB to where my init used to be. I did the little .mem .xrk test described in the link you gave and both file types did show up. 

It looks like a false positive. sorry to be a bother. I have a programmer family member who thinks no one deserves privacy but him.

whats not normal was the 2 java files that were suspicious.

---

### Post by bashiergui on 2014-02-10
IMO rkhunter and chkrootkit are not terribly user friendly. You're probably better off assuming all the warnings are false positives until proven otherwise. Make sure to follow the tutorials out there for both so that you are reducing the false positives you get with each scan. You need to baseline your system every time you update the kernel I believe.

---

