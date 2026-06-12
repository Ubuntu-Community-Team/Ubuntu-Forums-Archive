---
title: "GRUB thinks file system is ext2"
date: 2008-02-07
forum: General Help
---

### Post by mgaskell on 2008-02-07
Everything has been working fine on my desktop until today.

Grub loads but when Ubuntu is chosen, I get an error 17: cannot mount file system. Loading Super Grub from CD I have discovered that Grub thinks my Linux partition is ext2 when it has always been ext3. I think that's why I cannot mount the partition. Is there a way to make Grub understand that (hd0,1), my Linux partition is in fact formatted ext3?

Thanks in advance.

---

### Post by Herman on 2008-02-07
:) Hello mgaskell,
As far as GRUB is concerned, it makes no difference at all whether your file system is ext2 or ext3. An ext3 file system is actually the same thing as an ext2 file system with the addition of the journalling feature. Here's a link to support that statement, [Linux ext3 FAQ]("http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html"), particularly see the Questions and answers about converting from ext2 to ext3 and from ext3 back to ext2 again.

More likely you have some other problem.
Perhaps you had a kernel update and you have a /boot/grub/menu.lst file that has been edited previously without also editing the groot line.
Here's what to do if something like that has happened, [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD.

Maybe you are booting with a flash memory stick  or an added hard disk or something else has changed in the way your disks are set up.
This link might help you, [     Grub error 17]("http://users.bigpond.net.au/hermanzone/p15.htm#17").

Regards, Herman :)

---

### Post by mgaskell on 2008-02-07
Thanks Herman,

The only think I did differently today was accept the software update prompt. I did not know that the kernal would be updated. I'll try the link and see if your suggestion will fix it.

---

### Post by mgaskell on 2008-02-07
Thanks again Herman,

Somehow my menu.lst file in Grub was modified where both the Ubuntu kenrels and Windows were pointing to hd0,0. H changed all the Ubuntu root lines to point to hd0,1 and everything is back to normal.

Don't know if I should uncomment the groot line though.

---

### Post by Herman on 2008-02-07
:) No, you shouldn't uncomment the groot line, but just check that it is correct and up to date.

The groot line is used whenever there is a kernel update and the script 'update-grub' is run to create your new menu.lst file.

Does your groot line say '(hd0,0)'? 
If so then that's the cause of your problem. It could date back to something you did quite a while ago with adding or changing partitions somehow, restoring from a partimage backup or some such operation.
If you have had some need to edit your /boot/grub/menu.lst boot entries at some stage in the past and you also edited your groot line as well, then your changes to your boot entries will be persistent. If not then the same thing will happen again at every kernel update.

You should take a look to see if you need to edit your groot line to agree with your boot entries,[# groot=(hd0,1)]("http://users.bigpond.net.au/hermanzone/p15.htm#groot")

Regards, Herman :)

---

### Post by mgaskell on 2008-02-08
Yea, my #groot line entry was #groot=(hd0,0). I edited it to (hd0,1). I guess I'm good to go for future kernel updates.

Thanks again.

---

### Post by Herman on 2008-02-08
:) Okay, good, now your all set! 
You're welcome.
Regards, Herman :)

---

