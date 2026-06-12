---
title: "remove Ubuntu completely"
date: 2007-02-17
forum: General Help
---

### Post by jbeef86 on 2007-02-17
I want to completely remove Ubuntu from my hard drive and basically just reformat it. I am not running any version of Windows in a dual boot setup. How would I go about deleting all the files from the hard drive without a Windows XP disk? I am just trying to start off with a fresh clean hard drive.

Any help is appreciated.

---

### Post by ola on 2007-02-17
Hi!

If you choose to go without reinstalling your system completely you can start of by rewriting the master boot record (MBR). I know that can be done from the windows recovery cd (but I don’t have more information than. Check your manual for that… Sorry). Once the MBR is rewritten you should be able to boot into Windows without seeing Grub at boot (where you choose Linux or Windows today). Make sure you have this step completed before you delete the partition otherwise you won’t be able to read the Grub configuration files.

To delete the Ubuntu partitions you can use the Windows disk management tool (located C:\WINDOWS\system32\diskmgmt.msc). Start that and delete the Ubuntu partitions.

If you choose to reinstall Windows the Windows installer can handle this for you.

Hope that answers your question. 

Good luck and you are always welcome back to Linux or Ubuntu at a later time!

(Don't forget to backup all important files)

---

### Post by Swab on 2007-02-17
Use some utility to zerofill the drive.  Depending on the brand of your hard drive there may be a utility available for download from the manufacturers website.  For instance Maxtor has something called MaxBlast which should do the job, as far as I know it will work on other brands of hard drives also.

---

### Post by jbeef86 on 2007-02-17
Thanks for the reply Ola & Swab

The problem is that I forgot all my Windows cd's at work so I dont have that option for a couple of days. I wanted to reformat my hard drive with some kind of boot cd but the system boots right into Ubuntu and doesnt have an option of booting from a cd. I am totally new to Linux so this is also a problem. 

Swab I will look into that utility you mentioned. I cant find any information about wiping out a hard drive that has Linux installed as the only OS. Everything I find is dual boot with Windows and they either want to remove Linux or Windows.

Thanks for the ideas will keep at it.

---

### Post by cengelsma on 2007-03-09
I'm wanting to do the exact same thing as you, but I plan on installing a dual boot system.  

I have my computer's "Rescue and Recovery CD" but when I boot up with it, it gives me a mounting error.  Do I need to erase Ubuntu and then try the disk?  If so, how do I go about doing that?

---

### Post by kevinlyfellow on 2007-03-09
Stick in the Ubuntu cd, open up gparted and delete all the partitions

---

### Post by kevanr on 2007-03-09
What program can you use to purge a HDD? Like, rewrite the binary.

---

### Post by Alev on 2007-03-09
> **jbeef86 said:**
> 
I wanted to reformat my hard drive with some kind of boot cd but the system boots right into Ubuntu and doesnt have an option of booting from a cd.


Maybe your boot order is weird.  When I first tried to install ubuntu I couldn't get my computer to run the cd because the BIOS or whatever takes care of it was set to look to the hard drive before the cd drive.  Then again, if you already installed ubuntu that probably isn't it.  Maybe worth keeping in mind.

---

### Post by llamakc on 2007-03-09
> **jbeef86 said:**
> Thanks for the reply Ola & Swab

The problem is that I forgot all my Windows cd's at work so I dont have that option for a couple of days. I wanted to reformat my hard drive with some kind of boot cd but the system boots right into Ubuntu and doesnt have an option of booting from a cd. I am totally new to Linux so this is also a problem. 

Swab I will look into that utility you mentioned. I cant find any information about wiping out a hard drive that has Linux installed as the only OS. Everything I find is dual boot with Windows and they either want to remove Linux or Windows.

Thanks for the ideas will keep at it.

Set the BIOS to boot from CD first. Start up with the LiveCD in the drive.

Do you ONLY want to blank a hard drive, or do you intend to reinstall (something)?

You can use Gparted on the LiveCD to remove the partitions, create a single one, and format it to whatever filesystem you choose.

---

