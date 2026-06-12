---
title: "Dual boot question - A bit urgent!"
date: 2008-06-21
forum: General Help
---

### Post by xdavidx on 2008-06-21
Hi!I have 2 hard drives and i had(and have)WinXp installed in one of them and later i got Ubuntu installed on the other and it has created the dualboot option to select what i want to use and so far so good, but my doubt is: can i format the WinXp drive(because i'll use vbox from now on in ubuntu with winxp) and get no problems for doing a format to it?what i mean is if it will assume ubuntu as the "host" when i reboot and enter on it without having problems.

Thks.
By the way what are the best programs to format it trough Ubuntu?

---

### Post by geo909 on 2008-06-21
You should use gparted from a live cd. You can find gparted in ubuntu's live cd but there is a "gparted live cd" too.

 I guess what you should do is to erase your xp partition and resize ubuntu's so that it takes all the size of your disk.

Using gparted is very easy, it has a very user-friendly gui. It is also considered the classic tools (and quite safe) for such operations. Though, I would strongly advise you to back up your important files first.

 I use clonezilla livecd to make backup images of my internal hard disk. If you do erase and resize partitions, I would recommend using clonezilla first to make an image copy of your disk. This way, If something goes wrong you can restore things as they used to be before the repartitioning.

EDIT: sorry! I didn't read your post very well, you didn't talk about different partitions..
Yes, doing that with gparted should cause no problems.

Though, if you have a separate disk, it wouldn't harm you to leave XP, you don't know when you'll need them. Sometimes there are some copatibility issues (I was once given a cd that wouldn't mount in ubuntu because it was of a proprietary format for example), That is a personal thing though, this is just my opinion..

---

### Post by xdavidx on 2008-06-21
> **geo909 said:**
> You should use gparted from a live cd. You can find gparted in ubuntu's live cd but there is a "gparted live cd" too.

 I guess what you should do is to erase your xp partition and resize ubuntu's so that it takes all the size of your disk.

Using gparted is very easy, it has a very user-friendly gui. It is also considered the classic tools (and quite safe) for such operations. Though, I would strongly advise you to back up your important files first.

 I use clonezilla livecd to make backup images of my internal hard disk. If you do erase and resize partitions, I would recommend using clonezilla first to make an image copy of your disk. This way, If something goes wrong you can restore things as they used to be before the repartitioning.


thks, but i don't have any partitions, i have separated hard drives..anyway i've made backup of things first just in case.. but i can do it from ubuntu, the format?! iv'e installed gparted on it..my problem is if it will boot fine after i erase xp partition..i guess i'll have to try :P 
Thks for the tips ;)

---

### Post by geo909 on 2008-06-21
> **xdavidx said:**
> thks, but i don't have any partitions, i have separated hard drives..anyway i've made backup of things first just in case.. but i can do it from ubuntu, the format?! iv'e installed gparted on it..my problem is if it will boot fine after i erase xp partition..i guess i'll have to try :P 
Thks for the tips ;)

Yes, sorry, I have already edit my last post.
I don't think that there will be a problem

Anyway, since you don't erase any data in your ubuntu disk, I guess the worst that can happen to you is a grub issue which is easy to solve...

---

### Post by xdavidx on 2008-06-21
> **geo909 said:**
> Yes, sorry, I have already edit my last post.
I don't think that there will be a problem

Anyway, since you don't erase any data in your ubuntu disk, I guess the worst that can happen to you is a grub issue which is easy to solve...

yes, but i just want to install it on ubuntu cause it's annoying to have to reboot everytime, i just have xp installed from the beggining cause i am a graphic/web designer and i need macromedia programs..ubuntu have great programs but not the programs everyone use..so..i think i won't have problems..i'll give it a try :P 

thks for ur help, any problem i keep in touch ;) [[]]

---

### Post by xdavidx on 2008-06-21
i've made the format and when i restart it appears the dualboot list like before, i've changed the boot order on bios to start with the ubuntu drive, and it asks to "press a key to reboot" so my problem now is, how can i start my computer like it were a "clean install" without the dualboot list of kernels and winxp. since i haven't got xp anymore..

---

### Post by waspbr on 2008-06-21
there probably is a way of modifying your menu.lst to do that. 

alternatively you can just go to synaptic install startup manager, and once you have it installed, select the OS you wanna boot to and set the timer to 1 sec.

Although I find the boot list rather useful in case I have to boot in recovery mode, I just have to select the option. 

my 2 cents

---

### Post by geo909 on 2008-06-21
You can always modify the grub menu configuration file:
```
gksudo gedit /boot/grub/menu.lst
```
Firstly you erase the XP entry.
I guess you can also make it boot directly to ubuntu, but I'm not sure..

EDIT: Didn't understand.. You say that you can't actually boot to ubuntu?

---

### Post by issih on 2008-06-21
As a general rule, if you install windows first on one disk, then ubuntu on another, ubuntu defaults to placing grub into the master boot record (mbr) of the primary (windows) drive.

If you completely format the windows drive you may well find that you kill grub and therefore can't boot at all without some work.

Your simplest option is probably to install grub into the mbr of the ubuntu drive:

[https://help.ubuntu.com/community/GrubHowto#head-4c7a8640a439568ee312c9f262cc1099634f25ef](https://help.ubuntu.com/community/GrubHowto#head-4c7a8640a439568ee312c9f262cc1099634f25ef) 

Then set your bios to boot from the drive ubuntu is installed on.

Grub is fixed from the livecd environment, so it doesn't matter if you format the xp drive first, just be aware that you will probably have to do this step.

Hope that helps

---

### Post by xdavidx on 2008-06-21
> **geo909 said:**
> You can always modify the grub menu configuration file:
```
gksudo gedit /boot/grub/menu.lst
```
Firstly you erase the XP entry.
I guess you can also make it boot directly to ubuntu, but I'm not sure..

EDIT: Didn't understand.. You say that you can't actually boot to ubuntu?

No no, i can boot to it ;) u get it right. i've just edit the menu and i'm gonna restart now, to see what happens.

---

### Post by geo909 on 2008-06-21
Well, I guess it would be simpler just to set waiting time to 1 sec or something like that..

---

### Post by xdavidx on 2008-06-21
> **issih said:**
> As a general rule, if you install windows first on one disk, then ubuntu on another, ubuntu defaults to placing grub into the master boot record (mbr) of the primary (windows) drive.

If you completely format the windows drive you may well find that you kill grub and therefore can't boot at all without some work.

Your simplest option is probably to install grub into the mbr of the ubuntu drive:

[https://help.ubuntu.com/community/GrubHowto#head-4c7a8640a439568ee312c9f262cc1099634f25ef](https://help.ubuntu.com/community/GrubHowto#head-4c7a8640a439568ee312c9f262cc1099634f25ef) 

Then set your bios to boot from the drive ubuntu is installed on.

Grub is fixed from the livecd environment, so it doesn't matter if you format the xp drive first, just be aware that you will probably have to do this step.

Hope that helps

i understand what you said, but i've made a format of xp with gparted and it still to boot anyway..but i think if i wanted to "really have" like i said before a clean install booting from ubuntu drive i had to do that.
thks

---

### Post by geo909 on 2008-06-21
Nothing dirty in your installation! ;)
Don't think leaving grub is an issue.
Just change waiting time to 1 sec.

---

### Post by xdavidx on 2008-06-21
> **geo909 said:**
> Well, I guess it would be simpler just to set waiting time to 1 sec or something like that..

waspbr "Although I find the boot list rather useful in case I have to boot in recovery mode, I just have to select the option." 

i've followed his advise, but i edited like you said, just to take the winxp boot entry and the other old kernels.

So i guess is all cool :) , i just go to install xp right now.

thks for your help!! ;) [[]]

---

### Post by geo909 on 2008-06-21
If you install XP now while you have ubuntu you will have to reinstall GRUB.
Sorry, didn't understand that you would reinstall XP..

---

### Post by xdavidx on 2008-06-21
> **geo909 said:**
> If you install XP now while you have ubuntu you will have to reinstall GRUB.
Sorry, didn't understand that you would reinstall XP..

i will "reinstall" but is on Virtualbox inside Ubuntu, not in the same drive..

---

### Post by geo909 on 2008-06-21
Ok, sorry, I finally got it..

---

### Post by xdavidx on 2008-06-21
> **geo909 said:**
> Ok, sorry, I finally got it..

Ahah, that's okay no problem ;)

---

