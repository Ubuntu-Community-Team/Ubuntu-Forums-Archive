---
title: "Preboot encryption"
date: 2008-03-05
forum: General Help
---

### Post by justleen on 2008-03-05
Hey there Ubuntu's!

I got a few questions on encryption, hopefully some off you

can help me out with this...What I get from my Boss: A windows installation on two partitions, encrypted with "safeguard easy", including a preboot encryption.

What I want: Windows must stay (this is mandatory), and Ubuntu installed on it as my working env (yes, I can do without Windows.. but it must stay installed..). Both windows and ubuntu must be encrypted, with a preboot encryption in place.

What I have so far: I uninstalled safeguard, partitioned, installed ubuntu.
So i now have my dual setup, but no encrypted what so ever...

Since I really must have encryption, Im wondering what my options are

- reinstall windows MBR, add Ubuntu to it, use safeguard to encrypt preboot and windows
This leaves me with a not encrypted ubuntu.

- Reinstall ubuntu, using alt CD and create fulle encrypted ubuntu and preboot. Leave some space for windows, reinstall it, use safeguard to encrypt the partition
This works, but is quite a lot of work, since i need to image everything, and then hope i can return it in its org. state...


Does ayny one have an experience with this? If so, can you give me some pointers as to how to get this up and running??

Any tips would be appreciated, since if my Boss notices i dont have any encryption its gonna be Bye Bye Ubuntu, and Im back to windows + safeguard..

---

### Post by wieman01 on 2008-03-05
From what I know, there is no way you can have pre-boot encryption for dual boot systems. It's either pre-boot encryption for Windows or Linux, in either case you can install only either of them.

BUT... But... There is something called "Wubi" which lets you install Ubuntu on a Windows partition, which is then hosted in a separate file. I think that would work. That way you don't have to reinstall anything and simply install Ubuntu on "top" of Windows. Safeguard would then encrypt your Windows partition including Ubuntu.

[http://wubi-installer.org/]("http://wubi-installer.org/")

It is also simple to remove it afterwards which is a great benefit.

---

### Post by justleen on 2008-03-05
hhmm...cheers, that is a good idea indeed.

BUT.. if i add ubuntu to my windows boot loader, let safeguard encrypt windows MBR and the NTFS partition, that would give me a "pseudo" preboot for linux right?
(that the actuall ext3 partitions are not encrypted is fine, i can fix that with encrypted lvm's  for /home and /etc (all sensitive data will be there..)

---

### Post by wieman01 on 2008-03-05
Hang on... Since Ubuntu will reside inside your NTFS file system (i.e. inside Windows), it will be automatically encrypted, I mean the whole NTFS partition including the Ubuntu installation. 

However, now I am not so sure what will happen with the MBR and GRUB. Can they co-exist? Will Grub overwrite the pre-boot encryption loader? I wish I had a WIndows machine to test it.

Tell you what... you ought to really test it with a PC you don't really need anymore. I think it could work, but I don't know which part of the MBR Safeguard occupies and which part is allocated to GRUB. There could be a conflict and you might end up with a partition that is encrypted with no means to decrypt it.

But again, you Linux install will be securely locked inside the Windows partition which is protected by Safeguard. Interesting thought... Might be a beautiful and yet simple solution. IF it works.

---

### Post by wieman01 on 2008-03-05
And while we're at it, have a look at this article, a very interesting read if you have a few minutes:

[http://citp.princeton.edu/memory/]("http://citp.princeton.edu/memory/")

So encryption on portable computers can be quite a false friend.

---

### Post by edd8990 on 2008-03-05
Just a commenr (And this may be of no use whatsoever)

I currently have a dual-boot system, where the windows partition is encrypted (via Truecrypt's encrpyt system partition function) and Ubuntu is not (Yet - I'm still trying to find a way to move it to an encrypted volume without loosing my settings). Surely if the linux partition was to be encrypted, then this sould be the solution to what justleen wants. (As another aside, the current boot situation is this, the computer boots the harddrive which has the truecrypt bootloader installed on the MBR. At this point, I can either type in my windows password to get to windows, or press "esc" and I get forwarded to the grub bootloader [truecrypt has the ability to chainload partitions and boot off them sequentially].)

Also: on the harvesting of encryption keys from memory: Encryption is only really meant to protect your data when your computer is switched off (Or at least, the encrypted partitions are not mounted). If you're relying on encryption to protect your data when it's switched on/mounted, then you're doing it wrong!

---

### Post by wieman01 on 2008-03-05
> **edd8990 said:**
> Also: on the harvesting of encryption keys from memory: Encryption is only really meant to protect your data when your computer is switched off (Or at least, the encrypted partitions are not mounted). If you're relying on encryption to protect your data when it's switched on/mounted, then you're doing it wrong!
Very much so. That's the point of the article. I was just shocked to hear how simple it appears to be. I have read the entire article and I am sure any advanced PC user could do it.

---

### Post by justleen on 2008-03-05
one of the advantages of working in IT: plenty of test machines :)

I'll set something up here (disadvantage here, i have no connection to the internet "for security reasons"...I say to hell with security! :)

What Edd is describing would be sufficient. preboot through truecrypt/safeguard, encrypted windows disk, normal linux (with added encrypted partitions/volumes for data)

---

### Post by justleen on 2008-03-06
Wubi didnt work.. it gives me quite a lot of disk errors, hten fails half way during first boot of the Wubi-Ubuntu. Rebooting gives me a prompt, I can logon, but a lot s missing / is unconfigured (for example: i get a very odd keyboard layout, but when i try to reconfigure with dpkg-reconfigure console-data, it tells me console data is not installed)

I have a feeling Wubi is not liking my disk layout...

I tried to boot Ubuntu from the windows boot loader, this also without succes...( i get grub errors, or just a blank screen)

Thanks for the tips.. ill get back here when i found a solution

---

### Post by edd8990 on 2008-03-06
One thing I forgot to say before (sorry- I wan't thining straight!) If you're setting up Ubuntu with truecrypt encrypted XP, you need to move grub from the MBR before you install it. A simple guide on how to move it was posted [Here](http://ubuntuforums.org/showpost.php?p=4287308&postcount=9)

---

### Post by blgould on 2008-04-17
Having just set up another Linux variant as a VMWare (free version at [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)) Guest OS, hosted under WinXP, perhaps this may be a way to encrypt both OS's with a single pre-boot encryption product.  Just a thought.

Good luck with your project.

---

