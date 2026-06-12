---
title: "data recovery after burning iso as live drive to encrypted drive its stored on"
date: 2017-05-06
forum: General Help
---

### Post by thereal-alleycat on 2017-05-06
I'm not going to check if this is already posted since , frankly, i'm still trying to think how i have managed to do this while stone cold sober. Im not a total lamer to the linux world, i get around. I have performed several feats of data recovery using testdisk and the like in the past. Even after partitions and formatting, those tools perform miracles.

Now ...

I can provide you with all the screenshots i want. But im afraid how i did this without noticing is beyond my comprehension. I have managed to use usb writer (standard included tool) to write an iso of AVlinux which i wanted to test on a 32gb usb drive (more than enough to run linux) to the exact same **encrypted** drive it was stored on.

I didnt get any warnings and i noticed nothing until i tried booting from the usb drive i *thought* i installed it to.

i actually went out for a walk with my cat while it was writing, so, what i have now is a drive that was full of data but also consisted of one encrypted partition which now 
in disks has two partitions, one being the live iso i suppose and the other being "empty"
Testdisk says it finds nothing but maybe a file system with errors, i cant find anything to undelete, but it also wont restore the original partitions
since it was encrypted i can understand how it cant find files but im like hoping some guru somewhere on the planet would know how i can restore the partition and decrypt it with my passphrase so i can at least get **some** data back. Im not very hopeful and it still eludes me how this got done without notice or warning but it is what it is

if anyone has anything i would be **very** much obliged, theres some pictures on it that dont have anywhere else, i had some on onedrive but microsoft blocked that account for "no reasons given" 

anyone ?

---

### Post by yancek on 2017-05-06
Did you use a separate usb drive to write AVLinux to then boot it and install it to the 32GB drive?
Or did you write the AVLinux to the 32GB drive with usb writer?
Did you have a separate partition on the 32GB drive on which to install it so that you did not overwrite your encrypted data partition?

If you have another Linux system on the computer, can you run sudo fdisk -l or sudo gdisk -l and post the output here,  Make sure the 32GB drive is attached before doing this.

---

