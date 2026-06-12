---
title: "any way to control the filesystem scans when booting up?"
date: 2007-09-21
forum: General Help
---

### Post by mrsev on 2007-09-21
I have a problem that I think will have a simple solution but I do not know where to find it. 

My problem is this. I use my laptop on the move a lot and sometimes I will reboot more than 10 times a day. My problem is that I find that the filesystem checks are far too frequent and they get in the way of my work whilst I sit like a mug for ages whilst my entire filesystem is checked. 

It is even worse when I am sitting next to someone and need to show them something. I get conversations like this:

They> Whats that?
Me> Its linux.
They> Oh!
They> Er why is it taking so long?
Me> Well it needs to check the file system!
They> Er ..why?
Me> For errors and corruption in the journals and file system.
They> Hmm ..... Linux sucks.

Anyway the problem is this ...... I should be able to control when these checks occur. I should be able to abort a scan without problems and finally that there should be a simple way to do these things.

Anyone have any tips, tricks or apps that can help?

On a more informative note... can anyone tell me why it is needed to check a journalized filesystem so frequently? My understanding was that the point of a journalized file system was that this should not be needed. 

Cheers, 

Sev

---

### Post by NilsE on 2007-09-21
The checks are simply to verify the integrity of the file system.  I am not sure of how to interupt it. 

Anyway, here is the way to change the frequency.

FSCK Mount count command:

sudo tune2fs -c XX /dev/sdb2

XX = number of boots between checks. I made mine 50 but you can make it anything you like. I think the default was 30 or so.

---

### Post by mrsev on 2007-09-21
Thanks I will do the changes you suggest. 

However, I would really like to know how to control these things on a moment to moment level.

I just think  this is a major issue as far as usability goes. Especially as hard drives are getting bigger and bigger and it already takes a stupidly long time to boot when fsck runs first.

Does anyone know if I can just CTRL-C when it starts to do this. (I have not tried as I fear that this might hose my system)

It would be great to hear from others who might have solved this problem 

As a side note, I saw an app called bonager that might help so I will try it and post the results when I have tested it.

Ciao all

Sev


> **NilsE said:**
> The checks are simply to verify the integrity of the file system.  I am not sure of how to interupt it. 

Anyway, here is the way to change the frequency.

FSCK Mount count command:

sudo tune2fs -c XX /dev/sdb2

XX = number of boots between checks. I made mine 50 but you can make it anything you like. I think the default was 30 or so.

---

### Post by purplenite on 2007-09-21
Bonager works great for controlling those annoying scans. It tells you how many boots you have left until the next scan, and it can force a scan at the next boot (which resets the counter).

Unfortunately I don't think there is any app that will allow you to stop a scan in progress.

---

