---
title: "Dell won't boot from ANY cd"
date: 2008-06-07
forum: General Help
---

### Post by Mchl923 on 2008-06-07
I've tried about ten different linux distros and one xp install cd and not a single one will boot.  It tries but then I get "strike f1 to retry boot, f2 for setup utility."  CD drive is only enabled boot device.

---

### Post by cariboo on 2008-06-07
Once you're in an operating system, can the drive read CD's ?

Jim

---

### Post by Mchl923 on 2008-06-07
Yes it can, but it doesn't even sound like the disk spins before I get the error.

---

### Post by ChameleonDave on 2008-06-08
That's not even an OS problem, let alone an Ubuntu problem.

All you can do is look through the options in the BIOS until you work out how make it boot from a CD.  We can't see those BIOS screens to help you.

If it really is impossible, then it's a hardware problem.  Either open it up to move cables around, or return the machine to the vendor.

---

### Post by Mchl923 on 2008-06-08
I am aware of this, but the computer is way out of warranty and I don't know a better place to get help.  When you mention BIOS settings do you mean other than boot order/devices?

---

### Post by underdog512 on 2008-06-08
> **Mchl923 said:**
> Yes it can, but it doesn't even sound like the disk spins before I get the error.

What is the specific error that you getting?

---

### Post by Mchl923 on 2008-06-08
two beeps then:

> **Mchl923 said:**
> "strike f1 to retry boot, f2 for setup utility"

thats all the info I get

---

### Post by Mchl923 on 2008-06-08
*bump*

---

### Post by Tixer on 2008-06-08
What exactly are you trying to accomplish here? Do you want to install Ubuntu (in which case we can recommend other methods to do so) or what?

---

### Post by Mchl923 on 2008-06-08
Actually I want to reinstall windows on this computer (family computer, they don't like change) and I don't know how to do it without booting from disk.

---

### Post by Mchl923 on 2008-06-08
*bump*

I'm desperate here.

---

### Post by avtolle on 2008-06-08
OK, the beeps are an error code/alert. Since you are getting something on the screen, then you should take the action recommended. From reviewing one of your posts above, it seems you should press f2 to get into the set up utility. From there, it may be possible to alter the boot order; I don't know, and would have to be present looking over your shoulder to determine this. Or, you could press f1 to retry the boot. The beeps alert you to an error condition; the screen provides you with information as to what it is, as it has by stating what you posted. HTH.

---

### Post by Mchl923 on 2008-06-08
setup utility is just regular BIOS settings; all is well there (pretty sure)
When I retry I get the same error.  Boot order is CD first

---

### Post by Powerman2442 on 2008-06-08
My dad was having a lot of trouble with his old Dell and he told me to format the hard drive and start over. (He thought the hard drive was to full...) Keep on getting the the same message you were, F1 to retry boot or F2 for setup utility. 

After 6 hours of installing Windows XP (shouldn't be taking that long on any computer) I finally get XP up and running go to install some of his old programs and the first one locks up the computer. I was never able to successfully boot it again. I had to reinstall XP, again, with no luck.

This time, however, I kept getting blue screen error messages saying "Disk Write Error", etc. So I conclude that the hard drive is bad and needs replaced (almost 7 year old Maxtor). Barrow a Western Digital 40 GB ATA-100 off my uncle. Hook it up, load XP on it, and it is running like new. Using my uncle's old HDD until the new WD 80 GB comes in the mail.

Not sure but maybe you are having the same problem. I wasn't able to boot up any of my LiveCDs. Nothing... openSUSE 10.3, Ubuntu 7.04, Ubuntu 8.04, DSL, etc. Nothing would boot it would always "freeze". It did run Windows disks though, which is odd. :S Maybe Dell HAD something against Linux? Anyways, if you are having a similar problem to me try swapping the hard drive for another. Then again, not sure how old your Dell is. Ours is almost 7 years old.

Good Luck.

---

### Post by Powerman2442 on 2008-06-08
> **Mchl923 said:**
> setup utility is just regular BIOS settings; all is well there (pretty sure)
When I retry I get the same error.  Boot order is CD first

Yeah you can't edit anything in Dell BIOS but the Time/Date and the Boot Order. LOL Surprised you can even adjust the boot order. :(

---

### Post by ardvark71 on 2008-06-08
> **Powerman2442 said:**
> 
This time, however, I kept getting blue screen error messages saying "Disk Write Error", etc. So I conclude that the hard drive is bad and needs replaced (almost 7 year old Maxtor). Barrow a Western Digital 40 GB ATA-100 off my uncle. Hook it up, load XP on it, and it is running like new. Using my uncle's old HDD until the new WD 80 GB comes in the mail.


Hi...

Depending upon how old the motherboard is, you may have read/write issues with the 80 GB hard drive. Past a certain amount, older motherboards have a problem interacting with the newer hard drives. Not sure why, but I have seen it before with systems I have worked on. 

Best Regards...

---

### Post by ardvark71 on 2008-06-08
> **Mchl923 said:**
> setup utility is just regular BIOS settings; all is well there (pretty sure)
When I retry I get the same error.  Boot order is CD first

Hi...

If you're getting the same message after confirming the boot order, my first guess is your CD-ROM drive is bad, particularly if this happens with every CD you try. :(

You can probably pick one up pretty cheap at a second hand store or if you want to go brand new and don't mind the color of the face plate, there are some at Newegg that are good on the wallet...

[http://www.newegg.com/Store/Category.aspx?Category=10&name=CD-DVD-Burners-Media](http://www.newegg.com/Store/Category.aspx?Category=10&name=CD-DVD-Burners-Media)

Best Regards...

---

### Post by Ameneon on 2008-06-08
On pretty much any Dell system this side of the millennium you can choose which device to boot by pressing F12 during POST. But as mentioned earlier, if you cannot boot from any CD that boots fine in other systems (ie, you know they are bootable), then likely your optical needs to be replaced. In the vast majority of Dell systems that's a simple operation and the drive itself is fairly cheap.

---

### Post by Bari on 2008-06-08
However if the cd drive is duff don't do what I did and stick a dvd drive in instead of a cd drive. Although the drive worked fine when the os was running the bios refused to recognise it as it wasn't a cd drive and so wouldn't boot from it. It took me ages to find a little programme I could put on a floppy which would boot and give me options as to which divice to boot from.

---

### Post by wpshooter on 2008-06-08
> **Mchl923 said:**
> setup utility is just regular BIOS settings; all is well there (pretty sure)
When I retry I get the same error.  Boot order is CD first

Mchl923:

Have you checked the data and power cables on the CD-Rom drive to make sure they are properly seated/connected ?

If you have done the above, then go into the setup/BIOS and load all of the DEFAULT bios settings, save them and then see if it will boot to the CD-ROM.

---

### Post by Sef on 2008-06-08
Mchl923:

Don't bump a thread unless 24 hours have gone by.  Otherwise an infraction could be issued.

---

### Post by Powerman2442 on 2008-06-08
> **ardvark71 said:**
> Hi...

Depending upon how old the motherboard is, you may have read/write issues with the 80 GB hard drive. Past a certain amount, older motherboards have a problem interacting with the newer hard drives. Not sure why, but I have seen it before with systems I have worked on. 

Best Regards...

Anything up to 120 is fine on that mobo.

---

### Post by Mchl923 on 2008-06-08
> **Sef said:**
> Mchl923:

Don't bump a thread unless 24 hours have gone by.  Otherwise an infraction could be issued.

Thanks for the heads up, I'll watch that from now on.

As for the CD drive, could it still be the problem if it worked fine in the OS?

---

### Post by Mchl923 on 2008-06-08
Well, I switched the CD drive with an old one I had lying around, and... IT WORKED!!! awesome.

---

### Post by iwallet on 2008-06-08
can you take a picture of the screen while in the bios?! 
ive never heard of this problem before... have you tryed with an external cd reader?!

---

### Post by ardvark71 on 2008-06-08
> **Powerman2442 said:**
> Anything up to 120 is fine on that mobo.

Hi...

Ok, good. :) Just wanted to give a heads up.

Best Regards...

---

### Post by Mchl923 on 2008-06-09
> **iwallet said:**
> can you take a picture of the screen while in the bios?! 
ive never heard of this problem before... have you tryed with an external cd reader?!

Is there something specific you'd like to see in BIOS, because I don't think there is anything interesting there.

p.s.  I don't have any external cd readers.

---

### Post by Powerman2442 on 2008-06-09
> **Mchl923 said:**
> Well, I switched the CD drive with an old one I had lying around, and... IT WORKED!!! awesome.

So everything works fine with a different CD drive?

---

### Post by Mchl923 on 2008-06-09
yeah, it pretty much solved all my problems

---

### Post by Ameneon on 2008-06-09
Very peculiar that it should work in the OS but not to boot, unless it is just working partially in the OS, ie, showing TOC but not really being able to read much actual data or the like, then it could make sense. But glad that it worked for you at least :)

---

