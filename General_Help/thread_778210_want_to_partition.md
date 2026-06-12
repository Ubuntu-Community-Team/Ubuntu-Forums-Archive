---
title: "want to partition"
date: 2008-05-01
forum: General Help
---

### Post by stogchris81 on 2008-05-01
when i installed ubuntu it i lost vista. how do i find it, get to it? do i need to re-install it
?

---

### Post by NightwishFan on 2008-05-01
In ubuntu terminal paste this command and post the result:
```
sudo fdisk -l
```

---

### Post by stogchris81 on 2008-05-01
> **NightwishFan said:**
> In ubuntu terminal paste this command and post the result:
```
sudo fdisk -l
```
fdisk invalid option -- 1
usage: fdisk -b ssz  -u DISK... need more?

---

### Post by Monicker on 2008-05-01
> **stogchris81 said:**
> fdisk invalid option -- 1
usage: fdisk -b ssz  -u DISK... need more?

That fdisk option should be the letter "l", not the number "1".

---

### Post by NightwishFan on 2008-05-01
;] I said paste for a reason I guess I should point that out it does look like a 1.

---

### Post by stogchris81 on 2008-05-01
> **Monicker said:**
> That fdisk option should be the letter "l", not the number "1".  thank you.  there are 3. the first is linux 2nd is extended the 3rd is linux swap / solaris

---

### Post by stogchris81 on 2008-05-01
> **stogchris81 said:**
> thank you.  there are 3. the first is linux 2nd is extended the 3rd is linux swap / solarisby the way, i am not talking to you on the computer i am speaking of.

---

### Post by tommyhakinen on 2008-05-01
did you found something like this when you boot:
> 
....
Other Operating System
Microsoft Windows Vista


when you install Ubuntu, did you use the free space? (did you remember during installation that you did some adjustment on hard drive space?)
if not, probably you have installed it on the whole hard drive. I made this mistake too when installing Gutsy.

> **stogchris81 said:**
> thank you.  there are 3. the first is linux 2nd is extended the 3rd is linux swap / solaris
Looks like you have installed it on the whole hard drive. When this happened, your vista has been wiped out.

---

### Post by stogchris81 on 2008-05-01
> **tommyhakinen said:**
> did you found something like this when you boot:


when you install Ubuntu, did you use the free space? (did you remember during installation that you did some adjustment on hard drive space?)
if not, probably you have installed it on the whole hard drive. I made this mistake too when installing Gutsy.how do i partition again to install vista. unfortunately i am not pleased with linux and want vista back. i hope noone is offended by that.

---

### Post by NightwishFan on 2008-05-02
Not offended but I personally believe its a mistake you should install with wubi or dual boot if anything. I believe you can just install like normal and it will wipe linux although thankfully i know very little about how windows works.

---

### Post by stogchris81 on 2008-05-02
> **NightwishFan said:**
> Not offended but I personally believe its a mistake you should install with wubi or dual boot if anything. I believe you can just install like normal and it will wipe linux although thankfully i know very little about how windows works.
can i make a partition for windows from ubuntu? and how?

---

### Post by NightwishFan on 2008-05-02
You can use the partition editor on the ubuntu live cd but I actually am not sure if you can shrink your extended partition. Hopefully someone knows better than I. It sounds logical (haha logical ahem) that you could resize your logical ext3 partition and then resize the extended one then use the free space for an ntfs partition and install windows on that with the windows install disc.

---

### Post by stogchris81 on 2008-05-02
> **NightwishFan said:**
> You can use the partition editor on the ubuntu live cd but I actually am not sure if you can shrink your extended partition. Hopefully someone knows better than I. It sounds logical (haha logical ahem) that you could resize your logical ext3 partition and then resize the extended one then use the free space for an ntfs partition and install windows on that with the windows install disc.
honestly, i am not proficient enough to have even attempted to install a linuux much less learn to use it. where do i find the partition editor?

---

### Post by NightwishFan on 2008-05-02
System -> Administrator -> Partition Manager I believe (on live cd)

Edit: Linux isn't hard just stick with it, dont give up! Windows is hard as well especially to fix problems. Keep a dual boot so you can have what you are familiar with if all else fails and feel free to ask about any problems.

---

### Post by notesetter on 2008-05-02
Sorry that you're not satisfied with Ubuntu. If you use your Vista OS disk to install, it should completely destroy the existing data on your hard drive and install the Vista OS. Use the disk(s) labeled "Factory Restore" or something similar. If your computer came with operating system CD or DVD, you may need to install from that. You might need to create a "boot disk" first. Google "Vista Boot Disk" Also, make sure that the CD/DVD drive is set to boot from first in you BIOS.

If you want to install Ubuntu on a separate partition at a later time, check out this site. It helped me out (I'm new to Linux/Ubuntu myself)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Cheers,

Dave

---

### Post by stogchris81 on 2008-05-02
> **NightwishFan said:**
> System -> Administrator -> Partition Manager I believe (on live cd)

Edit: Linux isn't hard just stick with it, dont give up! Windows is hard as well especially to fix problems. Keep a dual boot so you can have what you are familiar with if all else fails and feel free to ask about any problems. cant find it.

---

### Post by stogchris81 on 2008-05-02
> **notesetter said:**
> Sorry that you're not satisfied with Ubuntu. If you use your Vista OS disk to install, it should completely destroy the existing data on your hard drive and install the Vista OS. Use the disk(s) labeled "Factory Restore" or something similar. If your computer came with operating system CD or DVD, you may need to install from that. You might need to create a "boot disk" first. Google "Vista Boot Disk" Also, make sure that the CD/DVD drive is set to boot from first in you BIOS.

If you want to install Ubuntu on a separate partition at a later time, check out this site. It helped me out (I'm new to Linux/Ubuntu myself)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) 

Cheers,

Dave i have tried and it wont let me install on the linux partition. o even tried to format and it gave me an error.

---

### Post by NightwishFan on 2008-05-02
Are you on the Ubuntu live cd? it should be there with either the name gparted or partition manager something along those lines.

---

### Post by stogchris81 on 2008-05-02
> **NightwishFan said:**
> Are you on the Ubuntu live cd? it should be there with either the name gparted or partition manager something along those lines. i inserted the dvd that i downloaded linux to and it is not there. is that the ubuntu live you are talking about?

---

### Post by NightwishFan on 2008-05-02
It should be. Although I cannot be sure do you have a full session of ubuntu that runs from cd? (you get a desktop)

If so open Applications -> Accessories? -> Terminal
type:
```

gparted

```
dont close terminal! if nothing comes up tell me what it says in the terminal

---

### Post by stogchris81 on 2008-05-02
> **NightwishFan said:**
> It should be. Although I cannot be sure do you have a full session of ubuntu that runs from cd? (you get a desktop)

If so open Applications -> Accessories? -> Terminal
type:
```

gparted

```
dont close terminal! if nothing comes up tell me what it says in the terminal
i wrote the ubuntu download to dvd.

---

### Post by NightwishFan on 2008-05-02
You need to boot from the dvd. Its called a live session.

---

### Post by stogchris81 on 2008-05-02
> **stogchris81 said:**
> i wrote the ubuntu download to dvd. the program gparted is not installed. you can install it by typing.....   i typed it and it said gparted is not available.

---

### Post by Freelance Physicist on 2008-05-02
Just in case there's some confusion, NightwishFan means that after inserting the Ubuntu installation CD or DVD, you should restart your computer and choose "Try Ubuntu without any change to your computer" at the first screen. The following link is a picture of what I mean: [http://tinyurl.com/68r68p](http://tinyurl.com/68r68p)

Edit: An important question: stogchris81, do you have the installation disk for Windows Vista or did you buy a computer with Vista already installed?

---

### Post by NightwishFan on 2008-05-02
My apologies if I was not clear I did not want to sound patronizing. It should be on the live session by default. Otherwise you can download a gparted live cd and burn it to and iso and boot from that to edit your partitions.

---

### Post by stogchris81 on 2008-05-02
> **stogchris81 said:**
> i wrote the ubuntu download to dvd.

> **Freelance Physicist said:**
> Just in case there's some confusion, NightwishFan means that after inserting the Ubuntu installation CD or DVD, you should restart your computer and choose "Try Ubuntu without any change to your computer" at the first screen. The following link is a picture of what I mean: [http://tinyurl.com/68r68p](http://tinyurl.com/68r68p)

Edit: An important question: stogchris81, do you have the installation disk for Windows Vista or did you buy a computer with Vista already installed? bought comp with vista installed, came with a vista cd.

---

### Post by stogchris81 on 2008-05-02
> **NightwishFan said:**
> My apologies if I was not clear I did not want to sound patronizing. It should be on the live session by default. Otherwise you can download a gparted live cd and burn it to and iso and boot from that to edit your partitions. dont worry about patronizing me my friend. i need all the help i can get.

---

### Post by NightwishFan on 2008-05-02
gparted live cd is here

[http://downloads.sourceforge.net/gparted/gparted-live-0.3.6-7.iso?modtime=1208153087&big_mirror=0](http://downloads.sourceforge.net/gparted/gparted-live-0.3.6-7.iso?modtime=1208153087&big_mirror=0)

---

### Post by stogchris81 on 2008-05-02
> **NightwishFan said:**
> My apologies if I was not clear I did not want to sound patronizing. It should be on the live session by default. Otherwise you can download a gparted live cd and burn it to and iso and boot from that to edit your partitions.

> **stogchris81 said:**
> dont worry about patronizing me my friend. i need all the help i can get.ok, i found the partion editor. now what do i do to find or re-install vista?

---

### Post by NightwishFan on 2008-05-02
2 ways:

Easy: (non dual boot way)
Delete all the linux (partitions ext3 extended and swap). Then reboot and use the windows install cd to install windows (crys a little inside). Optionally you can create a ntfs partition on the entire drive while in gparted but I dont know if that will help any.

Harder: (keeps both linux and windows)
Resize the ext3 partition and leave enough space for vista (i recommend 50gb) Then resize the extended partition so that all the space you made for vista is now empty (if you can resize extended partitions I have no idea i never tried) then install windows to the empty space and later I will help you reinstall grub to boot both of them since by default you can only boot windows even though linux is there.

---

### Post by stogchris81 on 2008-05-02
> **NightwishFan said:**
> 2 ways:

Easy: (non dual boot way)
Delete all the linux (partitions ext3 extended and swap). Then reboot and use the windows install cd to install windows (crys a little inside). Optionally you can create a ntfs partition on the entire drive while in gparted but I dont know if that will help any.

Harder: (keeps both linux and windows)
Resize the ext3 partition and leave enough space for vista (i recommend 50gb) Then resize the extended partition so that all the space you made for vista is now empty (if you can resize extended partitions I have no idea i never tried) then install windows to the empty space and later I will help you reinstall grub to boot both of them since by default you can only boot windows even though linux is there. i deleted the ext3 but it would not let me delete the extended and swap. im trying to reload vista now.

---

### Post by NightwishFan on 2008-05-02
Wait. You have to do "swapoff" on the swap partition then you are able to. I am sorry I just remembered that.

---

### Post by stogchris81 on 2008-05-02
> **stogchris81 said:**
> i deleted the ext3 but it would not let me delete the extended and swap. im trying to reload vista now.
how would i format that 1st partition to ntfs?

---

### Post by stogchris81 on 2008-05-02
> **stogchris81 said:**
> i deleted the ext3 but it would not let me delete the extended and swap. im trying to reload vista now.

> **stogchris81 said:**
> how would i format that 1st partition to ntfs?when should i have done the swap off?

---

### Post by stogchris81 on 2008-05-02
> **stogchris81 said:**
> when should i have done the swap off?it seems to be installing windows now.

---

### Post by NightwishFan on 2008-05-02
Grats. :)

When you have windows installed, if you want, copy the wubi.exe and install ubuntu with wubi as it is easily uninstalled and no partitioning involved. I highly recommend that if you ever want to try linux.

---

### Post by stogchris81 on 2008-05-02
> **stogchris81 said:**
> when should i have done the swap off?

> **NightwishFan said:**
> Grats. :)

When you have windows installed, if you want, copy the wubi.exe and install ubuntu with wubi as it is easily uninstalled and no partitioning involved. I highly recommend that if you ever want to try linux.i owe you so much. you have been very kind. can i ask you what that quote on all your replies means? the one about linus torvalds.

---

### Post by NightwishFan on 2008-05-02
No problem I am happy to help if i can.


It is a Chuck Norris style joke and a play on words. As Linus is the creator of the Linux kernel. The quote refers to the manual pages for command line bash commands. For example "man apropos" Will bring up a help page for the apropos command.

Heres some more:
Linus Torvalds is more powerful than root.
Linus only has 2 buttons on his keyboard &#8216;1' and &#8216;0'
Linus can divide by zero.

[http://pablogger.wordpress.com/2007/11/03/chuck-norris-vs-linus-torvalds/](http://pablogger.wordpress.com/2007/11/03/chuck-norris-vs-linus-torvalds/)

:lolflag: Enjoy

---

### Post by stogchris81 on 2008-05-02
> **NightwishFan said:**
> No problem I am happy to help if i can.


It is a Chuck Norris style joke and a play on words. As Linus is the creator of the Linux kernel. The quote refers to the manual pages for command line bash commands. For example "man apropos" Will bring up a help page for the apropos command.

Heres some more:
Linus Torvalds is more powerful than root.
Linus only has 2 buttons on his keyboard ‘1' and ‘0'
Linus can divide by zero.

[http://pablogger.wordpress.com/2007/11/03/chuck-norris-vs-linus-torvalds/](http://pablogger.wordpress.com/2007/11/03/chuck-norris-vs-linus-torvalds/)

:lolflag: Enjoy now i can get back to rocking guitar hero. again, THANK YOU SO MUCH!!!!

---

### Post by stogchris81 on 2008-05-02
> **stogchris81 said:**
> now i can get back to rocking guitar hero. again, THANK YOU SO MUCH!!!!
it took me a minute, but i got the play on words. haha. good night.

---

### Post by NightwishFan on 2008-05-02
Night, good luck.

---

