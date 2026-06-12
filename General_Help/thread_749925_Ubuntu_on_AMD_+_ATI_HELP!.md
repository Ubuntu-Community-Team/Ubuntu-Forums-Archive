---
title: "Ubuntu on AMD + ATI? HELP!"
date: 2008-04-08
forum: General Help
---

### Post by GavinRoskamp on 2008-04-08
Okay, so I have this Gateway laptop, it is the Gateway T-1620 to be exact.
It has Windows Vista Home Premium on it by default, and I REALLY want to get the taste of freedom on it, since my old Dell that ran it perfect died a while ago. :,(
Anyway, I need a way to get Ubuntu 7.04, 7.10, or 8.04 working on it.
With all of them, I get this window and a weird blue background and it says something like the X window manager can't be initiated, (Or something similar) and I can do absolutely nothing on it then.

I have tried Wubi as well as the alternative and normal versions of the AMD 64 (64-bit) and the normal one (32-bit) and I get the same thing every time.
Except in Wubi.
In there, I get this REALLY odd thing:
A black screen while booting, and then it gets stuck with some junk on it like it can't find any SCSI drives.

I am really going bonkers trying to figure this out, because I can't even get to the GUI in it!
I can't use Ubuntu to do anything like a regular computer on it, and I really need a way to get it working.

I hope you can help me out on this, because I am still a moderate-beginner in Ubuntu.
I know lots of stuff in Windows, but that doesn't help when you try to fight retarded pain in the *** companies like AMD and ATI.
Oh well.
Thanks for your time, community members, and I hope you can help me.
Cause if I don't get it working I think I will throw my laptop out the window in frustration with Vista!!!

Have I mentioned I hate Vista??
Yeah. :)
It drives me to the brink of insanity when it doesn't work, and it HOGGGGGGS memory!
I have 2 gig (shared, 1.6 gig system) of RAM, a 222GB hard drive, and an ATI Radeon graphics card with an AMD Turion 64 X2 Mobile Technology processor and a Realtek Wireless card. (It is either a dream, or I used like Ubuntu 6.06/6.10, but I remember trying to internet surf and the wireless card didn't work.

Anyway, if you want to know anything else, I will try to keep up with this post, but feel free to email me as well at [email]gavinstipsandtricks@gmail.com[/email] and I will be able to reply much faster.
If I don't get this working, I will..... well, you know what I wrote above.
Throw this computer out the window, set it on fire and roll over it with a combine!
Well, thanks in advance.

Sincerely,
A very anti-Gateway user and pro-Dell user,
Gavin Roskamp
[email]gavinstipsandtricks@gmail.com[/email]

---

### Post by Rocket2DMn on 2008-04-09
You should try a normal install again since Wubi is not an officially supported method.  Don't forget to check the md5sums on your .iso images, then burn at a slow speed like 4x to a cd-r to prevent write errors
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM") md5sum
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against

Once you get into the boot, if X is giving you problems, you should reconfigure using this guide - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

On a side note, I would take down your email address, it's not wise to make that publicly available, it makes you a target for spam (picked up by bots that surf the web looking for email addresses to add to spam lists).

---

### Post by GavinRoskamp on 2008-04-18
Okay, I got past the ATI X server thing that was giving me crap, and I installed it via the alternate installation cd...

But now, I overwrote Vista (lolz) and I need it back

I have rescued a partition with Vista on it and need to get a way to boot into it (I used GParted and TestDisk to do that stuff)

Will the Vista recovery DVD work, or do I need to buy something?

I boot the hard drive and it says

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 17

What's Error 17 mean?

Hope you can help me out!!!

I have accidentally deleted the Ubuntu partition in the recovery process, but I didn't even get to the GUI part before I destroyed Vista (Muahahaha lolz)

So yeah, I can do Ubuntu installation again, and I know what I did wrong, and I won't do it again, and I need to stop talking! lolz

and to sto psaying loloz


Well, I can't stop talking because I can't help it!!!!

I AM FREAKING OUT HERE!!!!!!!!!!!!!!!


I NEED MY FILES OFF VISTA BEFORE I SAY GOODBYE!!!!!

I NEED MY E-MAILS!!! I HAVE THOUSANDS!!!!

I HAVE HOMEWORK ON VISTA!!!!!!

Can you help?

THANKS!

Gavin

---

### Post by forrestcupp on 2008-04-18
GRUB was installed to the hard drive's MBR, but it uses settings found on your Ubuntu partition.  You deleted that partition, so that's why you get the error.  Since you don't have anything on there now, here is what you need to do.

First, boot to your GParted LiveCD and delete all partitions, then create one big NTFS partition.  Then boot to your Vista DVD and install Vista, which will work now because you have a big NTFS partition.  This should set the boot loader to boot Vista instead of a defective GRUB.

Now you can install Ubuntu.  This time choose the option to use your free space instead of the entire drive.  When you choose that option, it will ask you how much of the hard drive you want to partition for Ubuntu.  Then you should be good to go.

If you still have issues with ATI and getting to your desktop after the installation, we can help you with that, too.

---

### Post by GavinRoskamp on 2008-04-18
> **forrestcupp said:**
> GRUB was installed to the hard drive's MBR, but it uses settings found on your Ubuntu partition.  You deleted that partition, so that's why you get the error.  Since you don't have anything on there now, here is what you need to do.

First, boot to your GParted LiveCD and delete all partitions, then create one big NTFS partition.  Then boot to your Vista DVD and install Vista, which will work now because you have a big NTFS partition.  This should set the boot loader to boot Vista instead of a defective GRUB.

Now you can install Ubuntu.  This time choose the option to use your free space instead of the entire drive.  When you choose that option, it will ask you how much of the hard drive you want to partition for Ubuntu.  Then you should be good to go.

If you still have issues with ATI and getting to your desktop after the installation, we can help you with that, too.

Yeah, I know I could do that, but I need a way to like backup my entire vista partition so I can put everything back.

Is there a way to just delete GRUB without re-partitioning?
Or can I just make the vista partition fill the unallocated space, then it will work?
Please help!
Thanks

---

### Post by forrestcupp on 2008-04-19
You said you overwrote Vista.  If you really overwrote Vista, then you're screwed; you lost everything you had and you just need to reinstall it like I said.

But if you didn't really overwrite Vista, it's still there, and you just can't get to it because of the GRUB error, then there are ways to restore the Vista boot loader.  [Here](http://ubuntuforums.org/showthread.php?t=622828) is a post explaining how to get the Windows boot loader back by using your Ubuntu LiveCD.  You can also use [the Super Grub Disk](http://supergrub.forjamari.linex.org/) to restore the Windows boot loader.

But if you really *overwrote* Vista like you said, there's nothing you can do about it unless you want to pay some computer forensics expert a lot of money to try to extract your data from your drive.

---

### Post by GavinRoskamp on 2008-04-19
> **forrestcupp said:**
> You said you overwrote Vista.  If you really overwrote Vista, then you're screwed; you lost everything you had and you just need to reinstall it like I said.

But if you didn't really overwrite Vista, it's still there, and you just can't get to it because of the GRUB error, then there are ways to restore the Vista boot loader.  [Here](http://ubuntuforums.org/showthread.php?t=622828) is a post explaining how to get the Windows boot loader back by using your Ubuntu LiveCD.  You can also use [the Super Grub Disk](http://supergrub.forjamari.linex.org/) to restore the Windows boot loader.

But if you really *overwrote* Vista like you said, there's nothing you can do about it unless you want to pay some computer forensics expert a lot of money to try to extract your data from your drive.

New update:
I have recovered my Vista partition, thanks in part to GParted and TestDisk ( I will use those every time I have a problem now!!!) :) and so now all I need to do is figure out why Vista isn't bootin right.
I got rid of GRUB using the Vista recovery DVD, but I can't get Vista to boot right anymore.

My only alternative to getting vista to boot is to install it on a blank partition, then move everything off the old partition to the new one.

---

