---
title: "Im an idiot"
date: 2008-02-20
forum: General Help
---

### Post by googlegot on 2008-02-20
I just completly destroyed most of my modules in a strange series of events caused by my own stupidity.  I had attempted to roll my own kernel in the past and in the process linked the test build folder (/lib/modules/2.6.22.9testbuild) to my main kernel folder (/lib/modules/2.6.22-14-generic).  Weeks later I came back and decided to patch my bcm43xx wireless driver so I could better hack my own network.  I stupidly placed the patch in the linux source folder that i had used to make my test kernel (2.6.22.9testbuild) and did a "sudo make modules" followed by a "sudo make modules_install".  Now, normally this wouldnt have been a huge deal because all this would alter would be the testbuild kernel folder (/lib/modules/2.6.22.9testbuild), but I made that link earlier and now i screwed all of my modules.

Could someone kindly help me rebuild all of my original modules pretty please?  I have a lot of required data on this drive and i would like to get them off before a reinstall.

---

### Post by SpaceTeddy on 2008-02-20
if you want to reinstall, you do not need to repair your kernel at all. just boot the live-cd and mount the drive your data is on, then copy it to any external storage (usb, drive, network, burn-it... whatever)

after that, you are free to reinstall...

or did i understand you wrong ?

---

### Post by googlegot on 2008-02-20
thanks for the suggestion, i didnt even think of that, but i dont have an external hard drive and i would rather be able to recover than reinstall at the moment

---

### Post by SpaceTeddy on 2008-02-20
i don't really know how recover works... since you need a working kernel to do that. I have never done it with a system that broken... let's hope there are smarter people than me out there...

sorry :(

---

### Post by googlegot on 2008-02-20
I think I may have solved my problem (hopefully)

I copied my original config file from /boot into my linux source folder and renamed it .config.  then i did a make modules and it seems to be rebuilding all my lost modules so im crossing my fingers and toes and hoping a make modules_install will fix it

---

### Post by agim on 2008-02-20
make sure you let us know if it worked. Its an interesting problem.

---

### Post by googlegot on 2008-02-20
Unfortunately, that did not work, so I am just recompiling the entire kernel per generic ubuntu specs.  That should work.

---

### Post by googlegot on 2008-02-21
So I finally have it working again.  I had to compile my own kernel, install it, boot into it, open synaptics, and reinstall 2.6.22-14-generic.  After all that my system is finally back to normal.

A message to you kids out there: dont symlink your compiled kernel modules folder to your original kernel modules folder!  It will come back to bite you in the *** later.

---

