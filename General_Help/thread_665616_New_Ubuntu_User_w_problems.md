---
title: "New Ubuntu User w/ problems"
date: 2008-01-12
forum: General Help
---

### Post by Acal on 2008-01-12
Hey guys I am a new user... or soon to be user since I am having some difficulties installing any of the Ubuntu Distros. So I will let you in on my story and maybe you guys/girls could help me out a bit?  Well anyways it all started a few weeks ago when I got a devastating virus that made my PC unbearable and virtually unusable.  It was a fairly newly built PC so i decided what the heck and wiped my drive after a lot of trials and tribulations trying to fix the Virus.  After wiping my drive I decided to go for Linux and I did my research and I ended up deciding on Ubuntu.

 I copied Ubuntu and all other kinds of disks including Kubuntu, Open Suse and Mandriva, but they all resulted doing the same thing.  Everytime I would boot a disk, the disk would boot up with all the options, I would click on an option and my screen would just go black for a long while.  The closest I got to actually getting on was the Ubuntu 7.10 I386 disk which is weird because my CPU is an Athlon 64 X2, but the AMD64 disk just boots to a black screen as well.  I have tried them all and on all of them I get the option to boot install, but after I click on that the screen just goes black.  I obviously do not know the problem lol and I am seeking for your help, thanks.

Here are some of my system specs:( maybe it will help)

Video card: GE force 8800GTS 320MB
CPU: AMD Ahtlon 64 X2 6000+
Memory: 2 sticks of 1024 MB each

If you need other info fill me in and I will be glad to give you it.

Thanks for your help,

Acal :)

---

### Post by 4real*leb on 2008-01-12
Are you sure your not giving it enough time? Things tend to load very slowly with the CD.
Also try checking you disc for errors, it is one of the menu options.

---

### Post by ~LoKe on 2008-01-12
When the LiveCD boots and you get to the menu that says Start/Install Ubuntu, and a few more things, hit "F6".  A box will pop up with some text, in that box, change "splash" to "nosplash" or erase it altogether.

---

### Post by Jerry N on 2008-01-12
Have you tried booting the CD in the "safe video" mode?  That is the only way I can get an Ubuntu live CD to boot on my main computer with a dual core AMD64 processor and GeForce 7600 video. Some distributions refuse to boot at all.  I play with Linux on my secondary computer and haven't even tried to install it in my main machine yet.  

Jerry

---

### Post by danwood76 on 2008-01-12
You could try using the alternative install CD, this is an installer without the graphical portion and will allow you to install without video drivers.
You can then install the correct graphics driver as you go.

I had a problem install on an older machine that took around 15 mins to boot to the live desktop and sometimes not at all.
I had to disable the splash for it to boot at all.

regards,
Danny

---

### Post by Acal on 2008-01-12
> **4real*leb said:**
> Are you sure your not giving it enough time? Things tend to load very slowly with the CD.
Also try checking you disc for errors, it is one of the menu options.


Thanks for all the responses guys I appreciate the help.  Alright inserted the Ubuntu 7.10 amd64 disk and I followed your instructions. I typed in "nosplash" and it went straight to -Booting from Local disk....
with and underscore line flashing.  Do I just let it flash, because it is processing something or is it not supposed to take this long? 

Thanks, 

Acal

---

### Post by danwood76 on 2008-01-12
you need to press escape from that menu and type
```

live nosplash
```

You could press F6 on the safe graphics line and just delete the word splash in that line and press enter also.

it sounds like what you just did tried to make it boot from your hard disk.

regards,
Danny

---

### Post by Acal on 2008-01-12
> **danwood76 said:**
> you need to press escape from that menu and type
```

live nosplash
```

You could press F6 on the safe graphics line and just delete the word splash in that line and press enter also.

it sounds like what you just did tried to make it boot from your hard disk.

regards,
Danny

Yeah Danwood your right haha thanks for that insight, I did try booting from hard disk. So I restarted and  did what you told me " press F6 on the safe graphics line and just delete the word splash in that line and press enter also. " 

I believe it is going through the correct procedure now I have gotten as far as a tan screen with a mouse in the middle of it, but nothing else.  Now that tan screen just went black and its been like this for a bit. So I will try to wait this out.

 (Edit) Alright I have the Ubuntu Screen up, but when I click on Install in the desktop on the top it says Error! and prompts me to send an error report.  This is the furthest I have gotten so far so thank you very much! I'll keep toying with the install to see if it works.

By the way I am in the process of downloading the Alternative CD just incase this does not work out.  I might have to install through that.

Thanks, 
Acal

---

### Post by Acal on 2008-01-12
Unfortunately I have ran into another problem.  After setting my OS installation Preferences the Installation commences.  Once it hits 5% which reads to be - Creating ext3 File system for / in partition #1 of SCSI1 (0,0,0)...- It just freezes.  At first I thought it was just a long part of the installation process since someone gave me a heads up that it might take a while, but after 15 minutes of waiting and not being able to move my house or anything I do not think that is the case. :(

Anyone happen to have any insight on this matter?  The same thing happens when I try to install Kubuntu as well it stops at 5% and everything freezes. This is after I choose a guided format for the partition.

Thanks,

Acal

---

### Post by Acal on 2008-01-12
Anyone have any insight on this new problem I posted above? I don't want to clutter the forums with a new thread. Thanks

Acal

---

