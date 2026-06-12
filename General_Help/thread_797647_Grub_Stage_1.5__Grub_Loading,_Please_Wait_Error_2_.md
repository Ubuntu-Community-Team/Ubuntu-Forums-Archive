---
title: "Grub Stage 1.5  Grub Loading, Please Wait Error 2  &gt;???&lt;"
date: 2008-05-17
forum: General Help
---

### Post by pro003 on 2008-05-17
I have just installed gutsy on intel celeron 400MHz with 10GB HDD and 64MB RAM. There is no windows installation and Grub gets this error on boot:

```

Grub Stage 1.5

Grub Loading, Please Wait
Error 2

```

Anyone knows this issue? What should I do to resolve this?

---

### Post by overdrank on 2008-05-17
> **pro003 said:**
> I have just installed gutsy on intel celeron 400MHz with 10GB HDD and 64MB RAM. There is no windows installation and Grub gets this error on boot:

```

Grub Stage 1.5

Grub Loading, Please Wait
Error 2

```

Anyone knows this issue? What should I do to resolve this?

Hi and first off I do not believe that Gusty will run on that memory. and This link may help with the grub error
[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

---

### Post by kshane on 2008-05-17
> **pro003 said:**
> I have just installed gutsy on intel celeron 400MHz with 10GB HDD and 64MB RAM. There is no windows installation and Grub gets this error on boot:

```

Grub Stage 1.5

Grub Loading, Please Wait
Error 2

```

Anyone knows this issue? What should I do to resolve this?

I suggest you download Super Grub and burn it.  You can then boot up your system using it and repair the error.  I believe this error can be automatically fixed by Super Grub.

Kevin

---

### Post by pro003 on 2008-05-17
Thanks for your replies..

I got it somehow... I had to do some changes in BIOS so that drives would be recognized by AUTO > AUTO...

But on the other hand it's so slow that I'm getting sick of it... Would be worth to try some older version of Ubuntu for this kind of machine?

---

### Post by overdrank on 2008-05-17
> **pro003 said:**
> Thanks for your replies..

I got it somehow... I had to do some changes in BIOS so that drives would be recognized by AUTO > AUTO...

But on the other hand it's so slow that I'm getting sick of it... Would be worth to try some older version of Ubuntu for this kind of machine?

Hi and you could try feisty or even puppy, damn small linux. [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by mtschaef on 2009-08-13
I just had the same exact problem. (Error 2)
Hardware specs:
Dell Optiplex GX60 Intel Celeron 2.0 256MB 2100 RAM 500GB HDD

I was able to fix the problem by updating the BIOS from version "A00" to version "A09" from Dell's support website.
As soon as I updated the BIOS it worked like expected. No need to reinstall.
Hope this helps others...

---

### Post by bgiannes on 2009-09-24
i have the same error.


I have an old 370 pin MoBo (which i updated) i have a 200GB HD plug into an IDE controler card (as it can read larger then 137Mb).  It's a 1Ghz Pent III w/ 512Mb, ubuntu 9.04 server install.

grub boots correctly, then stops at error 2.

I'm using UUID to id the drive, 

Note:- The HD +install came out of another Pent III i had.

please help :confused:

---

### Post by Shadow Warrior on 2011-05-06
> **bgiannes said:**
> i have the same error.


I have an old 370 pin MoBo (which i updated) i have a 200GB HD plug into an IDE controler card (as it can read larger then 137Mb).  It's a 1Ghz Pent III w/ 512Mb, ubuntu 9.04 server install.

grub boots correctly, then stops at error 2.

I'm using UUID to id the drive, 

Note:- The HD +install came out of another Pent III i had.

please help :confused:
I'm having the same problem with my IBM ThinkPad. Regardless of what version of Linux that I attempt to install, I have the same problem. In one instance, it moves one more step to give me a menu of options; but, keyboard is locked up. See my Post over in the Installation Forum for more details.

---

### Post by ZenMasta on 2011-12-01
I know this is an old thread but I just encountered this problem on a system with 10.04 which has been running great for a long time. The today I get this. The only thing installed recently (today) was Firefox 8 (finally upgraded from 3.x)

CPU is Intel Core 1.86 GHz and 1gb memory. This PC is used for web and email only. Please advise

---

