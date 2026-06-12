---
title: "I'm desperate to make an ISO."
date: 2008-07-01
forum: General Help
---

### Post by Josdell on 2008-07-01
Hi everyone. I'm running Hardy Heron, and as far as I'm concerned, for me, it has been impossible to make a distributable ISO of my system. Don't tell me about about remastersys as for some reason when I type: 
```
sudo remastersys dist
```
I get a message which pretty much means that customdist.iso wasn't created when remastersys tried to. I'm guessing this is because I don't have mkisofs installed. So I try to run sudo apt-get install mkisofs, and it tells me it is replaced by genisoimage. I already have genisoimage installed too. I also installed the updated version of remastersys that doesn't ask for mkisofs at install, still no ISO. So I created a symbolic link that when a program asks for mkisofs, it gives it genisoimage. The link is broken, I don't know why. I tried reconstructor, no luck. I tried to make an ISO with genisoimage with the ISOTMP folder of remastersys after it failed, I don't even know if I did it right. I'm just here asking for the simplest solution to any of these problems with remastersys or any other simple way of creating a distributable version of my system with my /home/****** folder. I've been killing myself for 3 days. I just need some help. I don't know why these things are happening, I just want to make an ISO, remember I want it to be distributable. Also, on a side note, can someone tell me the process of running an ISO file with qemu?

Any help would be appreciated, along with some thanks to anyone who attempts to help. Thanks.

---

### Post by Bubba64 on 2008-07-01
I don't know the answer to your problem but after Hardy is installed it is over 4 gigs to big for a CD, maybe a thumb drive or DVD would work.

---

### Post by MrSootentai on 2008-07-01
I am in the same exact situation with ISO problem, can anyone help me out??

---

### Post by aeiah on 2008-07-02
have you tried just installing mkisofs like it asks?

[http://cdrecord.berlios.de/old/private/mkisofs.html](http://cdrecord.berlios.de/old/private/mkisofs.html)

---

### Post by realzippy on 2008-07-14
Check the size of your /home folder... !
Also had problems,because of too much music and video stuff,
after reducing /home to less about 200 Mb there was -wonder-
a file "custom.iso" in my remastersys folder!!
And was installed 20 minutes later on my old machine..after reinstalling the nvidiadriver it was perfect.
Suggest you delete the symbolic mkisofs links you made,the problem is not
genisoimage nor missing links...

---

### Post by silkstone on 2008-07-14
^^^^^^ Agreed. You should also check the .thumbnails folder and subfolders which may contain thousands of files. You can delete them and they will be recreated next time you browse image files.

The problem with disk images is that they don't distinguish between system and data files, unless the software lets you exclude specific data folders.

---

