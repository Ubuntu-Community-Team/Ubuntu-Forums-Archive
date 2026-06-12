---
title: "Trying to decide on whether to use encryption and encryption choice"
date: 2016-06-20
forum: General Help
---

### Post by jub2 on 2016-06-20
I'm fairly new to Linux, having recently installed Xubuntu on my secondary computer. I'm coming from Windows 7 and am familiar with Truecrypt and have used it to encrypt file containers, non-system partitions and operating system partitions. I've managed to use it for nearly a decade without ever losing data, so I'm not a newb to encryption. But looking at dm-crypt and LUKS has got me wondering if I can handle encryption in Linux!

I'll describe what I'm trying to do and would appreciate some feedback on suitable options.

I have 2 computers - my primary computer is a desktop currently running Windows 7 and I'd like to move this to Xubuntu 16.04 as host and Windows 7 as guest (VirtualBox VM). My secondary computer is a laptop that runs Xubuntu 16.04 as host with Windows 7 as guest (VirtualBox VM).

On the laptop, I use GPT partitioning and LVM, and would like to use the same on the desktop.
[HR][/HR]
_Encryption:_
Encrypting the entire system would be nice, and this is what I have with Truecrypt - encrypted system partition and non-system partition (marked as 'system favorite') - when I boot the computer and enter the password, the system partition and non-system 'system favorite' partition are decrypted and mounted. Very easy.

System encryption isn't a huge deal for the desktop since I view risk of someone stealing or otherwise physically accessing the desktop as very low. And I can use encrypted containers for data I want to protect - though I've found container encryption is more of a hassle than system encryption because you have to mount and enter password every time you wish to access the data, while with system encryption, it's a one-time password entry when powering on the system. Also, with file container encryption, since some of the data I wish to protect must reside on the VirtualBox virtual disk, I'll have to install encryption software onto the Windows guest. With system encryption of the host, I'm guessing decryption of the host would decrypt the virtual disk, so no need to run separate encryption software on the Windows guest and the entire encryption process is invisible to the guest since all VirtualBox ever provides the guest is an unencrypted virtual disk.

System encryption becomes a bigger concern for the laptop where risk of theft is considerably higher. Similar to the desktop, the alternative to system encryption would be encrypted file containers in both the host and the guest. I could enable a BIOS password, but any remotely savvy thief will just remove the disk, thus bypassing the BIOS password protection.

_LUKS:_
As I understand it, support for dm-crypt/LUKS is built into Ubuntu 16.04 (and the various flavors such as Xubuntu), and I understand that it may have a speed advantage over a Truecrypt style encryption solution, such as Veracrypt. Seems there is not much in the way of GUI management and the user mostly ends up using the terminal to manage it. The thing that scares me most about LUKS is the warning I found in the cryptsteup FAQ: [LUKS on partitions or raw disks?]("https://gitlab.com/cryptsetup/cryptsetup/wikis/FrequentlyAskedQuestions"):
[B]
Be aware that if you add LVM into the mix, things can get very complicated. Same with RAID but less so. In particular, data recovery can get exceedingly difficult. Only do so if you have a really good reason and always remember KISS is what separates an engineer from an amateur. Of course, if you really need the added complexity, KISS is satisfied. But be very sure as there is a price to pay for it. In engineering, complexity is always the enemy and needs to be fought without mercy when encountered.[/B]

Yikes! :eek:  

_Veracrypt:_
For my use, Veracrypt has the advantage of being familiar, since it is a fork off the discontinued Truecrypt project. It can also encrypt/decrypt existing system partitions, and has a very easy to use GUI. My concerns with Veracrypt are:
1. does it play well with LVM?
2. is it noticeably slower to read/write than LUKS?

---

### Post by sudodus on 2016-06-20
If you think the risk of physical access is small with the desktop, you can consider using no encryption. Remember that attacks via the internet connection are not prevented by encrypting the entire system, because it is unlocked when running the computer.

Encryption makes recovery much more difficult, and you should plan for a ***good backup method and to take backups regularly*** - and you should test that it really works (restoring from the backup to a 'third' drive, where the first drive is the internal drive and the second drive is where you store the backup).

-o-

I am not a security expert and leave to other people to answer your questions at the end of the opening post.

---

