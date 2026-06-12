---
title: "Dual Boot Problem w/ WXP &amp; Ubuntu 7.04"
date: 2007-09-08
forum: General Help
---

### Post by karl_stade on 2007-09-08
Hi all,

Second post here, third day using Ubuntu 7.04, loving it all so far. :)

Just a few issues I am having, that I have searched rigorously through this forum to solve, but I have not found anything that directly helps me. Let me explain more:

I am currently using my Dad's PC, on which I have installed a extra hard drive that I scored from work, and on this second (slave) hdd I have installed the lovely Ubuntu.

So it's all running nicely, managed to get the graphical effects working, printer is go, music is playing, IM is working... so far so good.

As this computer is my Dad's I have left the copy of Windows that was originally on this PC fully intact on the primary hdd, so he can still use it when he needs to do his stuff.

My problem is that on boot-up, I get the GRUB (I believe that that is the correct name) menu that asks me what O/S I would like to load. This menu has Ubuntu and a variety of recovery/safe modes to also choose from, which I can select up and down using my PS2 connection for my keyboard. The last item on the menu is the copy of Windows XP, which if I move the highlight down and press enter it will load it up fine.

The issue is, that if I start the PC up and just leave it it will load into Ubuntu after a set amount of time (about 10 seconds I believe), as Ubuntu is the default O/S on the GRUB menu. That is an issue for me, as my Dad has problems enough just doing word processing in Windows, and asking him to have to manually intervene to select and load Windows is taking it's toll on his patience.

So the real question is: Is there any way I can change the O/S boot preference to be set to Windows XP, so all he has to do is turn the computer on, wait an extra few seconds and then it will load into Windows like normal? And if I want to use Ubuntu all I have to do is intervene and select it from the menu before it loads into Windows.

If there is a way, I would very much know how to go about doing it, as if I can't get it sorted it will mean Ubuntu has to go, as it it is his computer after-all... and that's no fun for anyone now is it? I'm REALLY liking Ubuntu so far, it has excelled much more than I expected. 

Your help, assistance, input, and support on this matter is most appreciated.

It might also be worth mentioning that I probably only have a couple of days to have this sorted before he looses his patience and  have to sort it out any way I know how. :(

Thanks!

-Karl

---

### Post by rsambuca on 2007-09-08
Very easy fix...  You just have to change a few options in a file called the menu.lst which is what grub gets it's boot instructions from.  To do this:

Open a terminal and enter ```
gksudo gedit /boot/grub/menu.lst
```

Then find the line that says

default     0

You just have to change the number zero to point to the windows partition.  Just note that the numbers start at zero (not 1), and it also counts every row that says "title" as an option.  You will have a line in there that says "title  Other operating systems:", which gets counted.

You might also consider changing the "timeout" option down to 2 or 3 seconds so that your dad doesn't have to wait too long before it automatically boots into Windows for him.   That still gives you plenty of time to hit an arrow key to stop the timer and select your ubuntu OS.

EDIT:  Just for clarification:  If you have 3 ubuntu options (ubuntu, ubuntu recovery mode, and memtest) and the Other OS line, and Windows at the end, you will want to set the default number to "4"

---

### Post by karl_stade on 2007-09-08
Thanks! I knew it would be simple, but for a person who has only been using Windows O/S for over 10 years it can get a little confusing. But it's ok, I am willing to learn.

I will try it out and see how I go, and then post the results.

---

### Post by karl_stade on 2007-09-08
UPDATE:

SOLVED, Followed instructions exactly and it all went ok.

One thing, in the GRUB menu it has the following entries to select:
Ubuntu, Kernel 2.6.20-16- generic
then the recovery mode of that
then is has underneath:
Ubuntu, Kernel 2.6.20-15- generic
and also the recovery mode of that

then Memtest and Windows.

Why would I have v. 16 and 15 on the menu? What is the difference? I have only ever loaded v. 16 so far.

---

### Post by Casull on 2007-09-08
> **karl_stade said:**
> Why would I have v. 16 and 15 on the menu? What is the difference? I have only ever loaded v. 16 so far.

I believe the older version is just there.  I've tried loading the older kernels and have gotten a kernel panic; I say to therefore just delete the v15 lines, or at least comment them out.

---

### Post by karl_stade on 2007-09-08
Or just leave them there and not use them...

---

### Post by rsambuca on 2007-09-08
Just a few points to keep in mind...

If there is a kernel update, then your grub menu will be updated and you will have to change the default number line again.

The old kernels are not required (if you are positive that your new kernel works perfectly).  It is strange that the OLD kernels give you an error, but in any event, it doesn't matter.  Like a previous poster said, you can just put a # sign in front of all of those lines, or delete them entirely.  You will then have to change the default line again after this.  Also, they will re-appear after the next kernel update and you will have to remove them from your menu.lst again.  An alternative to this is to remove them completely.  You can open your synaptic package manager and search for linux-image and remove the old kernels.

---

