---
title: "Fedora 9 and Ubuntu on Same hard drive"
date: 2008-05-29
forum: General Help
---

### Post by melenor on 2008-05-29
My friend suggested that i try out fedora 9, and i decided to try it out but i don't really like the Live CD option so i want to install it to the hard drive, and i was wondering if i am going to shrink the ubuntu partition and install Fedora 9 on the new one is there anything i am going to need to do before i can install Fedora 9, My biggest worry is GRUB will it see both, Ubuntu and Fedora 9, or will i have to restore GRUB? Thanks.

---

### Post by bingoUV on 2008-05-29
Your biggest worry is baseless as fedora installer will retain Ubuntu's entry. 

But, I suggest before going through all the hassle of resizing your partitions, try fedora 9 in a virtual machine. Install virtualbox from [http://www.virtualbox.org/](http://www.virtualbox.org/). Download DVD iso. Without burning to a CD, boot a virtual machine with fedora. If you dislike live CDs because of speed, you will not dislike virtualbox. It is as fast as native.

Remember to update fedora 9 as soon as you install it in virtual machine. Fedora is generally released with a few rough edges.

When you are ready to install fedora on real hard disk, fedora gives a cool method to install from an ISO file lying on a hard disk partition, while you boot from a USB pen drive ([http://forums.fedoraforum.org/forum/showpost.php?p=915687&postcount=9](http://forums.fedoraforum.org/forum/showpost.php?p=915687&postcount=9))

---

### Post by melenor on 2008-05-29
can i use the Virtualbox in ubuntu?

---

### Post by bingoUV on 2008-05-29
yes, of course. Choose Ubuntu, and version from the download page.

---

### Post by melenor on 2008-05-29
okay i actually after trying for a little while installed it but however it didn't let me boot into ubuntu, so i restored grub and can't boot into fedora i know that the Fedora is on (hd0,2) how can i had that to the grub menu list?

---

