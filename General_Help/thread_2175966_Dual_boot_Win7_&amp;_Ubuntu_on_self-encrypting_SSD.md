---
title: "Dual boot Win7 &amp; Ubuntu on self-encrypting SSD"
date: 2013-09-22
forum: General Help
---

### Post by Jake the Peg on 2013-09-22
Hello,
My work will provide me with a Dell Latitude 6430u laptop. I have the option for this "Self-Encrypting" SSD: "*256GB Self Encrypting Mobility Solid State Drive Opal Standard Compliant" *which is optional, but I like the idea. 
It will arrive with Windows 7 already installed and I wish to repartition the SDD to add Ubuntu for dual boot:

[LIST]
[*]Windows 7 on c: already installed, don't want to touch this if possible other than shrinking it (existing partition 1)
[*]Ext4 Ubuntu LTS on Ext4 (new partition 2)
[*]NTFS Media partition for shared files and Win7 My Documents (new partition 3)
[/LIST]
I've installed set ups like this on classical non-encrypting HDDs, but don't know if this new type of self encrypting drive complicates the process. 

*Questions:* 

[LIST=1]
[*]Does the self-encrypting SSD create problems for booting up an Ubuntu CD/USB to partition and install in this dual boot configuration?
[*]Once installed, after entering the master password during boot up, do I arrive at grub as normal to select Win7 or Ubuntu?
[*]Any other considerations or words of advice?
[/LIST]
Thanks,
Jake

---

### Post by TheFu on 2013-09-22
I wish I knew, but don't you need another encrypted partition for swap?

---

### Post by Mark Phelps on 2013-09-22
> Any other considerations or words of advice?

Yeah -- check with the IT folks, or your Management, at work -- BEFORE you attempt to do this.

After all, it's THEIR property not yours, and they might be adverse to you making changes to it.

One more thing -- I've been issued several work laptops over the years, and in ALL cases, admin rights were locked out -- preventing just the kind of changes you want to make.  So, it might not even be possible to do what you want.

---

### Post by TheFu on 2013-09-22
> **Mark Phelps said:**
> Yeah -- check with the IT folks, or your Management, at work -- BEFORE you attempt to do this.

+1. Definitely!  Long time ago, I got a new laptop at work, took it home and added it to my home domain. See, laptop users were giving local admin rights because switching network settings required it back then.  Anyway, when I brought the laptop back to work on Monday, it wouldn't connect to AD and I was locked out from access to 80% of the systems needed for my job.  Called the IT helpdesk and they remoted in ... odd how they could do that without the machine being on the domain ... and re-added it.

OTOH, it sounded to me in the OP that this was allowed.  Encrypting storage on every portable device should be corporate IT policy, IMHO.  Where I work now is a tiny company with 20+ yr people, no less. We don't purchase devices for our people since each is so very picky that we'd make nobody happy. We are BYOD for everything except servers, which I run.  End users have Macs, Dells, i-Whatevers, Android, WM7 ... and we all used to have blackberries before the company started taking off.  I've never used firmware encrypted storage - though it has always been temping to see a BIOS screen demand access to storage. Seems like the encryption would happen before booting the boot loader to me.

I have purchased things from [these folks]("http://addonics.com/category/encryption.php"), but never the encrypted stuff.  My external infiniband storage is from them.  It it over 6 yrs old - probably free besides loose SATA cables in the first few months.

---

### Post by Jake the Peg on 2013-09-22
Hi,
This was certainly authorised - thanks. My query is technical - can I boot up from a CD/USB to install? I was hoping that someone may have had a similar experience with this type of SSD.

Jake,

---

### Post by Jake the Peg on 2013-09-22
> **TheFu said:**
> I wish I knew, but don't you need another encrypted partition for swap?

This should be set up automatically during the install. And there should be no need to encrypt anything at the level of the ubuntu install because the SSD hardware is encrypted. My post relates to the nature of the this hardware level encryption; this should remove the need to encrypt anything again afterwards (encrypted home folder, truecrypt folders etc.)

Thanks,
Jake.

---

### Post by XBNCPRk on 2013-09-22
Just from the description of 'self-encrypting' it sounds as though the SSD handles its own encryption/decryption on a hardware level. In other words, any software run from it is decrypted by the time it hits the cpu to be executed and thus wont have any problem. The encryption on the ssd is simply so I cant rip it out of your laptop, and shove it into a test frame to start reading your files without going to the trouble of 'guessing' your user login.

This is the only way they would be able to make a product like that. Otherwise every single program, every webpage addon, every script, etc that you ever run over the life of the machine would have to be able to handle someone elses proprietary encryption. 

So, yes, the ssd will function the exact same as any other.

---

### Post by Jake the Peg on 2013-09-22
Thanks for your replies so far. 
From Wikipedia:
[http://en.wikipedia.org/wiki/Hardware-based_full_disk_encryption](http://en.wikipedia.org/wiki/Hardware-based_full_disk_encryption)

There is a worrying section which suggests booting from CD or USB and modification (partitioning/installation) of the drive will be problematic:
**Protection from Alternative Boot Methods**
Recent hardware models circumvents booting from other devices and allowing access by using a dual Master Boot Record (MBR) system whereby the MBR for the operating system and data files is all encrypted along with a special MBR which is required to boot the Operating System. All data requests are intercepted in the SED firmware and will not allow decryption to take place unless the system has been booted from the special SED operating system which will then load the MBR of the encrypted part of the drive. This works by having a separate partition, hidden from view, which contains the proprietary operating system for the encryption management system. This means no other boot methods will allow access to the drive

Jake

---

### Post by Jake the Peg on 2013-09-23
I found the post below which shows it is possible, but one needs to boot the live CD/USB drive **after** the first boot step has completed the unlocking process. This is done by waiting until the windows boot sequence starts, then reinitating it, having first set the bios to be able to boot from these media. So not straightforward, but seems possible.


[https://plus.google.com/103342596752795218521/posts/Aaku51Ejbu7](https://plus.google.com/103342596752795218521/posts/Aaku51Ejbu7)


Jake

---

