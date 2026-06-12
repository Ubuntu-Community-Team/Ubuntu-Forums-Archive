---
title: "startup issues in 7.04"
date: 2008-05-06
forum: General Help
---

### Post by nandan on 2008-05-06
I have MS Win XP, 7.04 and 7.10 installed on separate partitions and i use GRUB to select the Os at startup.When I select 7.04, I can see the ubuntu logo and see the OS loading, but once the status bar is 'filled', I end up with a blank screen and nothing happens. I have to eventually do a power off to restart and sometimes, even after that, the problem persists, so I have to do this three-four times till I see the wallpaper. Starting in recovery mode works better, but even then, it  sometimes does not load.
I notice this problem has cropped up after installing 7.10...is it a coincidence? Even if it is not so, what is the issue? How can I solve it?
Would appreciate help on this matter...

Thanks!

---

### Post by overdrank on 2008-05-06
> **nandan said:**
> I have MS Win XP, 7.04 and 7.10 installed on separate partitions and i use GRUB to select the Os at startup.When I select 7.04, I can see the ubuntu logo and see the OS loading, but once the status bar is 'filled', I end up with a blank screen and nothing happens. I have to eventually do a power off to restart and sometimes, even after that, the problem persists, so I have to do this three-four times till I see the wallpaper. Starting in recovery mode works better, but even then, it  sometimes does not load.
I notice this problem has cropped up after installing 7.10...is it a coincidence? Even if it is not so, what is the issue? How can I solve it?
Would appreciate help on this matter...

Thanks!

Hi and I have had this issue with multiple versions of Ubuntu and I just removed the quiet splash from the kernel. You can try and press esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash. then if that works you can just edit your grub menu list.

---

### Post by nandan on 2008-05-07
hi and thanks for your reply. I am pretty much a non-technical guy, so would be great if you explain the procedure in a little more detail regarding how to remove the quiet splash from the kernel...

thanks once again!

---

### Post by overdrank on 2008-05-07
> **nandan said:**
> hi and thanks for your reply. I am pretty much a non-technical guy, so would be great if you explain the procedure in a little more detail regarding how to remove the quiet splash from the kernel...

thanks once again!

HI and I will try. When you reach the grub where you select the operating system to boot. Highlight the one you wish to boot to and press esp key. It will open another screen and I think it is the second choice and you highlight it then edit that line by pressing e.Then you can remove the quiet splash. Then if that works you can just edit your grub menu list and for editing the grub this is a good link. 
[http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu](http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu)

---

### Post by nandan on 2008-05-08
Thanks! it seems to have worked!:)

---

### Post by nandan on 2008-05-09
Well, it has not worked :( ...It worked for 5-6 reboots, but after that, it was the same problem!! Could somebody please help??

---

