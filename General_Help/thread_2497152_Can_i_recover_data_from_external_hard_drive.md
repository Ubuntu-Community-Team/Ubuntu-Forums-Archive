---
title: "Can i recover data from external hard drive?"
date: 2024-04-25
forum: General Help
---

### Post by robertseal149 on 2024-04-25
My external hard drive data has been lost, anyone know how to recover it?

---

### Post by ajgreeny on 2024-04-25
Tell us more!
We need a lot more detail if we are to help you as there are many, many things that might have gone wrong and without that detail we will be guessing. 

What exactly do you mean by lost? Did you forget the files were there and format the disk or has it just stopped working,  showing nothing in the file manager.
Can you mount the disk?
Do you see any error messages when you attempt to ue it and see your files?
What sort of disk is it, a flash-drive, spinning hard disk or a solid-state hard drive attached by USB?

---

### Post by Rubi1200 on 2024-04-25
Just to add to what **ajgreeny **has already said:

1. stop **all **write activity to the disk
2. what types of files were there, text, image?

---

### Post by TheFu on 2024-04-25
> **robertseal149 said:**
> My external hard drive data has been lost, anyone know how to recover it?

[LIST=1]
[*]Buy a new HDD.
[*]Use the backups you made from before the disk failed ( or ran off? - You did say it was "lost" ) to restore any files you don't want to lose.
[*]If the HDD is still under warranty, follow their RMA process to get a replacement.
[*]
[/LIST]

This has been the method for 40 yrs. Nothing new.  There isn't any magic.
BTW, I had an 8 month old HDD, with a 5 yr warranty, fail, about 3 weeks ago. Mailed the RMA yesterday.  Thankfully, I had backups or it is likely all that data would be gone.

Google found this: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
It isn't easy and can be a huge amount of work to get a bunch of generically-named files back.  There will be 20+ versions of each file, if any are recovered. For tens of thousands of files, each with multiple versions discovered, you'll never be able to determine the last version and keep only it.  That assumes the files you really, really, really, want back are even available.  But you have to try it yourself before you'll believe me.  I had to learn the hard way too.  In the end, I decided that having excellent backups is well worth the cost and relatively minimal time to setup compared to trying to use any of the data recovery tools to attempt getting just a few files back, much less all of them.

---

### Post by dragonfly41 on 2024-04-26
This site is a long, long shot and I have not used this product .. but if the data is valuable I would give it a punt.

[https://www.grc.com/sr/testimonials.htm](https://www.grc.com/sr/testimonials.htm)

---

### Post by TheFu on 2024-04-26
> **dragonfly41 said:**
> This site is a long, long shot and I have not used this product .. but if the data is valuable I would give it a punt.

[https://www.grc.com/sr/testimonials.htm](https://www.grc.com/sr/testimonials.htm)

I have a license and used Spinrite for a few years.  All it does is exercise the disk, just like doing weekly backups would.  Disks have built-in smarts that will notice when a specific area is having trouble being read. It will refresh those areas as the first step. If that fails, it will reallocate the area and mark it not to be used.  This has been built-into every HDD for over 20 yrs now.  Do you need a $100 piece of software that requires running from a dedicated OS to exercise your HDD?  No.  Also, it is really inconvenient when we have simple tools that will do the same thing on any Unix/Linux system.  

Spinrite violates the first rule of data recovery.  NEVER, EVER, try to write to the disk that is failing.  Talk to any expert in data recovery - you know the guys the FBI and NSA and insurance companies use - those guys have $10K recovery rigs that are setup with the "write" pin removed to prevent any chance of writes going back to the disk.

The best tool I know to actually recover data from a HDD is **ddrescue**. I think the package is gddrescue.  There's another ddrescue, which adds to the confusion.  I think they both work the same way. Perhaps one is a fork of the other, IDK.

Spinrite shows what consistently accessing drives (he markets it as a "scan test") will get the drive firmware to accomplish.  There are lots of other ways to achieve the same goals ... like running backups, weekly and running SMART tests periodically.  But Steve will happily take your money, if you like.  There are worst people to give money to, that's certain.  If it works for your needs, it is money well spent.

As I've learned more and more over the decades, I'm firmly in the "have good backups" camp and you'll not need to worry about failing disks very much.  You'll sleep better and isn't $50-$100 for a 2-4TB USB backup storage device worth that anyway?  I know it was for me.  Today, I have about 25TB of backup storage ... that goes with about 25TB of main storage.  I still have a little RAID, but backups are 1000x more useful and more important than RAID storage. Of that, I'm 100% certain.

And if nobody said this - never use a tool like spinrite on any flash storage. That means thumbdrives or SSDs or CF cards - don't use spinrite on them unless you want to drastically reduce the lifespan.

---

