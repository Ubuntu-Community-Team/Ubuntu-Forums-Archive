---
title: "HELP! My Vista stopped working!"
date: 2008-01-20
forum: General Help
---

### Post by taehC on 2008-01-20
I changed some partitions around(I didn't move the start of any of them) and now all of a sudden i cant boot into vista.  i can only boot into xp and vista.  in the partition table it says vista longhorn loader but when i actually hit enter on the option it says windows xp.  what do i do!!!

---

### Post by talsemgeest on 2008-01-20
Well if you want to reinstall the vista bootloader use the instructions at [http://members.rushmore.com/~jsky/id39.html]("http://members.rushmore.com/%7Ejsky/id39.html")

Hope this helps...

---

### Post by taehC on 2008-01-20
AH!!! I JUST CHECKED AND UBUNTU ISN't WORKING EITHER!!!
they both say NTLDR is missing.
Plz HELP!

---

### Post by shadyedsan on 2008-01-20
windows strikes again i think

is it an upgrade version of vista?

---

### Post by forestpixie on 2008-01-20
you've got a problem if booting ubuntu says it's missing ntldr :D

what exactly did you do because
> I changed some partitions around covers a whole multitude of sins

boot into you're livecd - open a terminal and post 

```
sudo fdisk -l
```

then you need to open nautilus and open the partition which your ubuntu install lives on - navigate to /boot/grub open menu.lst and post that as well

if you've a copy of supergrub boot with that and it should get you into ubuntu to start with

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by taehC on 2008-01-21
here is what i get when i type sudo fdisk -l
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38dacce1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       26109   209720511    7  HPFS/NTFS
/dev/sda2   *       26110       49296   186249577+  83  Linux
/dev/sda3           49297       60613    90903802+   7  HPFS/NTFS
/dev/sda4           60614       60801     1510110    5  Extended
/dev/sda5           60614       60801     1510078+  82  Linux swap / Solaris

```

---

### Post by taehC on 2008-01-21
ans also under boot there is no grub which i even know is CLEARLY wrong but i dont know how to fix it...
and i already got a super grub disk

---

### Post by taehC on 2008-01-21
anyone?

---

### Post by taehC on 2008-01-21
plz can anyone help?

---

### Post by talsemgeest on 2008-01-21
To restore the grub check here:[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)

---

### Post by taehC on 2008-01-21
i didn't get all that he said.  like how do i mount the partitions? it said to mount them 
/
/boot
/swap
but how?
oh and when i try to boot my linux partition it says the partition cant be mounted

---

### Post by talsemgeest on 2008-01-21
Sorry, my mistake. Forgot to add that you should follow the instructions on the second post, by remmelt. Also try running grub install and grub configure. I noticed those are two things that get run during ubuntu's install, so its worth a shot... Also read the rest of the posts for more info and methods.

---

### Post by wonnage on 2008-01-22
I can be 100% certain you either changed the partition order around or made a typo somewhere in your post. Your ubuntu entry is actually trying to boot your XP installation, which gives you the NTLDR error. Boot up super grub disk and use /dev/sda2 as the partition to boot from, and you should get into your linux install (assuming that's your linux boot partition).

Getting vista to boot on the other hand, is a world of hurt usually. You're best off just using the vista cd doing the automatic startup repair. It'd probably be easier in the future to download EasyBCD or something so you can make the vista bootloader handle your other OSes.

---

### Post by talsemgeest on 2008-01-22
To fix the vista bootloader see my first post

---

### Post by taehC on 2008-01-22
> **wonnage said:**
> I can be 100% certain you either changed the partition order around or made a typo somewhere in your post. Your ubuntu entry is actually trying to boot your XP installation, which gives you the NTLDR error. Boot up super grub disk and use /dev/sda2 as the partition to boot from, and you should get into your linux install (assuming that's your linux boot partition).

Getting vista to boot on the other hand, is a world of hurt usually. You're best off just using the vista cd doing the automatic startup repair. It'd probably be easier in the future to download EasyBCD or something so you can make the vista bootloader handle your other OSes.

ya the linux partition doesn't say that.
it says that partition cannot be mounted.

---

### Post by taehC on 2008-01-22
so ya i am still pretty much no where...

---

### Post by talsemgeest on 2008-01-23
Just reinstall the vista bootloader, check it works, and then reinstall the grub. Simple.

---

### Post by ele_mugv on 2008-01-23
> **talsemgeest said:**
> To restore the grub check here:[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)
had the same prob..i'm using ubuntu 5.10 sever edition, it never got to the desktop..what ubuntu version are using..i'v been advised to use 7.10, they say it's good with vista!!

---

### Post by taehC on 2008-01-23
i am using 7.10 
and i dont get how to reinstall the vista bootloader. i checked your link and did not get what they were saying.  and i have tried to reinstall grub... multiple times...

---

### Post by talsemgeest on 2008-01-24
Ok, boot into the vista dvd. Go through the options until you can click "repair this computer" or something like that. Click on the command prompt, and type "Bootrec.exe /FixBoot" and then "Bootrec.exe /FixMbr" . That should let you boot into vista.

---

