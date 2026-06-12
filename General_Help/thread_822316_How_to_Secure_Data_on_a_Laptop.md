---
title: "How to Secure Data on a Laptop?"
date: 2008-06-08
forum: General Help
---

### Post by jbrice on 2008-06-08
I'm trying to set up Ubuntu on a laptop for business use and am amazed that it still doesn't offer some easily set up form of encryption of user data (i.e. home folder contents) "out of the box". 
I have looked around and found a lot of options, but none that seem to be satisfactory as they either don't work with Hardy, or involve what are for me rather arcane and over-complicated procedures for encrypting whole partitions etc.
Has anyone found a way to do this that doesn't require a black belt in Ubuntu wrangling? If I can't crack this one it's going to have to be back to one of Mr. Gate's products in order to ensure my clients' data doesn't go astray.

TIA 

James B.

---

### Post by bingoUV on 2008-06-08
Will you be ok with Fedora 9? Encrypted filesystem by a checkbox during install process. [http://fedoraproject.org/wiki/Releases/9/FeatureList](http://fedoraproject.org/wiki/Releases/9/FeatureList)

---

### Post by jbrice on 2008-06-08
> **bingoUV said:**
> Will you be ok with Fedora 9? Encrypted filesystem by a checkbox during install process. [http://fedoraproject.org/wiki/Releases/9/FeatureList](http://fedoraproject.org/wiki/Releases/9/FeatureList)

Thanks, I'll take a look, but my feeling at the moment is that a fully encrypted file system is overkill. I'm also not comfortable with the idea that _everything_ is encrypted.

James B.

---

### Post by bingoUV on 2008-06-08
I can understand that. You can specify only a specific partition to be encrypted. Generally /home , /var and /etc could contain sensitive information, so make separate partitions for them and encrypt them. Or create a certain partition to store sensitive information.

It is more important to backup encrypted partitions than plain ones because one single byte change can screw up your whole data. Backup over VPN or when you are inside company network.

---

### Post by jbrice on 2008-06-09
I happened upon the following recently published blog -  ["Encrypted swap and home partition in Ubuntu 8.04"]("http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu")
Although not exactly quick or simple - it does offer a step-by-step procedure and also appears to meet my need.

I'm not really in a position to know how technically competent or secure this approach actually is - so would appreciate comments.

James B.

---

### Post by /etc/init.d/ on 2008-06-09
> **jbrice said:**
> Thanks, I'll take a look, but my feeling at the moment is that a fully encrypted file system is overkill. I'm also not comfortable with the idea that _everything_ is encrypted.
Then don't expect full data security or anything near it.

Just encrypting your home folder does not provide full protection of your data and won't stop a knowledgeable attacker.  There are many ways that data will "leak" out of the home folder and get onto other partitions:  the swap file being an obvious one.  There are also other less obvious ways, like temp files and scraps of your data going into /tmp,  crash dumps saved into /var/crash.  


All of these things can contain sensitive data "leaked" from your /home directory.  Not to mention that if you use hibernation with an unencrypted swap file, the encryption key is written to disk in plain text. 

If you want confidence in data security, encrypt everything.

---

### Post by bingoUV on 2008-06-09
If you don't consider this requiring a black belt in Ubuntu wrangling, do this. Note that troubleshooting it will be slightly tougher than initially setting it up. Updates of the packages necessary for this, or kernel updates might cause strange behaviour. Especially as it is not an Ubuntu out of the box feature. Not trying to scare you out of this.

To be safe, at least encrypt stuff outside /bin, /boot, /lib, /sbin and /usr. To be even safer, encrypt everything.

SWAP: In these days of abundant RAM, it is an option to not have swap at all for security reasons. Anyway swap is much slower than RAM. If accessing it also entails CPU overhead of decrypting, one more reason to get rid of it. Will the method support hibernating to encrypted swap?

---

### Post by /etc/init.d/ on 2008-06-09
> **bingoUV said:**
> Will the method support hibernating to encrypted swap?
Some tutorials set up the swap partition in such a way that it is initialised with a new key at every boot-up.  At shut-down, the key is forgotten and any swap data is now lost because the key was lost.

In such a configuration, it is not possible to use hibernation.

I don't know if there is a way to have some sort of boot-loader and use the same key to encrypt everything in Linux, which would allow hibernation.  At least when I experimented with Linux disk encryption some time ago, there was not such a way.  Things may now have changed.

However, even on operating systems with plenty of WDE software, like Windows, hibernation is flaky, and bugs sometimes cause system memory to be written to disk unencrypted (TrueCrypt did this sometimes up until recently.)

---

### Post by bingoUV on 2008-06-09
This guy [http://forum.fedoraforum.org/forum/showpost.php?p=974686&postcount=2](http://forum.fedoraforum.org/forum/showpost.php?p=974686&postcount=2) says he has done it. So we both are a bit behind the times :)

I totally agree with the flakiness of hibernation in most computers.

---

### Post by tact on 2008-06-09
> **bingoUV said:**
> Will you be ok with Fedora 9? Encrypted filesystem by a checkbox during install process. [http://fedoraproject.org/wiki/Releases/9/FeatureList](http://fedoraproject.org/wiki/Releases/9/FeatureList)

Encrypting at install time is available in ubuntu also for the past couple of releases.  You need to use the alternate installer CD not the live (desktop) CD.

If you are doing a simple "use whole disk" type of clean new install its very simple to install.

I wanted something a little more complicated and so manually handled all the partitioning.  I have / (root), swap, and /home on separate logical volumes inside a single encrypted container.  Of course /boot cannot be encrypted and so it is on a separate unencrypted partition.   

Thus everything other than /boot is encrypted.   So no need to worry about unencrypted swap or tmp files laying around.  I am only asked for one passphrase, once, at boot right after grub does its thing.

I have been running this kind of "whole disk" encryption for a year now, with Gutsy first, and now with Hardy.  This is on my corporate provided laptop.  I have not had any issues.  

I do keep my /home backed up to another (external-USB) encrypted HDD regularly.  And my company stuff (a subset of /home) is also regularly backed up to a company file server whenever I am in the office.  (so the office stuff is backed up in two places).

Whenever I connect the external-USB drive (its a collection of logical volumes inside a single encrypted container also) both Gutsy and Hardy had the smarts needed to pop up a dialog box informing me that the connected drive contains an encrypted container and prompts me for the passphrase. 

Once I enter the passphrase for the encrypted external drive I can then mount it and access it as if not encrypted at all.

Its all very slick.  But there are dangers.  One danger is that if that portion of the HDD that contains vital encryption information is damaged you lose the lot - no chance of recovery.   (This can be a good or a bad thing.   The bad not so bad if you have backups.)

---

### Post by Rainstride on 2008-06-09
download the alt copy of hardy and use the (easy) text installer, theres an option for setting up an encrypted install. im using it right now.:)

---

### Post by tact on 2008-06-09
> **bingoUV said:**
> This guy [http://forum.fedoraforum.org/forum/showpost.php?p=974686&postcount=2](http://forum.fedoraforum.org/forum/showpost.php?p=974686&postcount=2) says he has done it. So we both are a bit behind the times :)

I totally agree with the flakiness of hibernation in most computers.


Hibernation and suspend and of course resuming from either state - all works perfectly on my Dell laptop with full disk encryption.

Prior to  Hardy - suspend/hibernation never worked properly even with no encrypted partitions for me...  But with Hardy its all sweet!

---

### Post by bingoUV on 2008-06-09
Cool. I must have missed the news. Maybe because the alternate installer is a bit low profile?

I have a liveCD ISO. Can I use it as an alternate installer by giving some option during boot? It is a hassle to download a whole new ISO.

---

### Post by bingoUV on 2008-06-09
> **tact said:**
> Hibernation and suspend and of course resuming from either state - all works perfectly on my Dell laptop with full disk encryption.

Prior to  Hardy - suspend/hibernation never worked properly even with no encrypted partitions for me...  But with Hardy its all sweet!

The fact that we are discussing it proves that in general computers are not good at hibernating reliably ;). My custom made linux friendly computers have also reliably hibernated and resumed unless I screw them up. This is since Feisty/Fedora Core 6. There is always the heart stoppage when you try it for the first time in a newly installed/upgraded OS.

They were without encryption.

---

### Post by Rainstride on 2008-06-09
> **bingoUV said:**
> Cool. I must have missed the news. Maybe because the alternate installer is a bit low profile?

I have a liveCD ISO. Can I use it as an alternate installer by giving some option during boot? It is a hassle to download a whole new ISO.

you need to download it. its easy, go here [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) just under the green download button theres a check box for alt copy. or you can get the torrent file for it.

---

### Post by jbrice on 2008-06-11
With the encouragement offered here I have now reinstalled using the encrypted disk method. As this replaces _everything_ on the hard disk, I copied all the existing partitions on to an external USB disk using GParted before installing.

Having left the USB disk attached during the install, the installer found the copy of the original Ubuntu install on USB disk and added it to the Grub boot menu. Very conveniently this allows me to boot back into the old installation when I need to check out how I had it set up. It's then easy enough to delete the Grub menu items pointing to the external disk when I have done.

On the downside, this mode of installation zaps other partitions that you might want to keep - Dell diagnostics partition in my case - and also seems to rule out dual-booting.

---

### Post by tact on 2008-06-11
I believe that dual booting is supported but you need to choose the right option when it comes to the partitioning part of the install.  

I cannot remember all the options and what they are literally called...  but I am sure there is one called "use entire disk for encryption" and of course that will wipe out all other partitions.  (It warns you that will happen too).

There are other options that allow you to choose what partitions are kept etc...

Anyways..  whats done is done.  :)   You now have a fully encrypted (except /boot) system.  Congrats.  Enjoy.

---

### Post by anindya_m on 2008-06-11
Anyone here heard of CFS (Cryptographic FileSystem)? The package is cfs. It runs a daemon and can be installed separately without any reformatting. It can be used to encrypt just the contents of a particular directory, and is quite easy to use. See this site for a howto (skip the install section): [http://www.ibiblio.org/pub/Linux/docs/faqs/security/Cryptographic-File-System]("http://www.ibiblio.org/pub/Linux/docs/faqs/security/Cryptographic-File-System")

---

### Post by jbrice on 2008-06-11
An afterthought - any recommendations for backup up the fully-encrypted installation?

James B.

---

### Post by anindya_m on 2008-06-11
CFS is good for backup too, because you can just rsync the changed files to your backup disk. It is also completely portable across linux distros (can just store the folder on a CD). Again, no formatting is needed.

---

### Post by tact on 2008-06-11
> **jbrice said:**
> An afterthought - any recommendations for backup up the fully-encrypted installation?

James B.

I have an external (USB) drive that I use to do a full system back up.  (I just use the commandline "dd" utility to make a full sector by sector clone of the internal HDD - once only).  It ends up bootable and also fully encrypted, a total clone of the original drive, and so is available to me should the internal HDD ever die totally.  On my laptop its just 2 screws and the drive bay pops out and I can replace the internal drive.

Subsequent to the once-only cloning of the internal drive I then do regular backups of /home using (g)rsync to update changed files from the internal drive to the external drive.  

Business related folders, subsets of /home, also get backed up to corporate file servers (windows based servers) across the company LAN using (g)rsync.

If you don't feel the need to have a "ready to boot" encrypted HDD on standby in case of disaster - but still want the data encrypted in the place where the back up is stored.....then its easy to create an encrypted container on an external HDD and make that the destination for your backups (using any normal backup tool).  Of course this is easier but the external drive only has data and will not be bootable.

---

### Post by tact on 2008-06-11
When your fully encrypted system is booted up and running it transparently decrypts whatever is needed for any operation.  So any normal back up tool will work just fine, same as it will work for a non-encrypted system.   

If the back up destination is not a fully encrypted HDD, or an encrypted container,  then your backup will NOT be encrypted.

---

