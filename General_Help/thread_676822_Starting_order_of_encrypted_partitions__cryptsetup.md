---
title: "Starting order of encrypted partitions // cryptsetup, swap"
date: 2008-01-24
forum: General Help
---

### Post by megandy on 2008-01-24
Hi all,

after an (automatic) upgrade of cryptsetup the starting order (prompt for decryption) of my cryptodisks has changed. This seems to be the reason why my system fails to resume from hibernate.

I have 2 encrypted partitions (set up at installation time of ubuntu). One is the swap whereas the other is my home directory. Before the recent upgrade of cryptsetup a password prompt appeared just after loading of grub (when the splash screen is shown). After entering the password the system continued loading until a prompt for my /home appeared.

old starting order:
mounting of encrypted swap
booting
mounting of encrypted home

After the recent upgrade to cryptsetup_1.0.5-ubuntu2.1 both prompts appears after some time of booting - just at the same point where my home-disk was decrypted.

current starting order:
booting
mounting of encrypted swap
mounting of encrypted home

Entering both passwords leads to the following message:

* sdb5_crypt: the check for '/dev/mapper/sdb5_crypt' failed. /dev/mapper/sdb5_crypt contains data: - The device /dev/mapper/sdb5_crypt contains a valid filesystem type suspend.
followed by a message that indicates, that my home couldn't be mounted.

But the system does not resume. Has anybody an idea?
__________________

---

### Post by tact on 2008-01-24
I probably am not going to be of any real help to you.  Sorry about that.  But i am interested in any posts I see about HDD or partition encryption.

Recently (a few months back) decided to give the "encrypt whole disk from install" feature that is available with Gutsy a go.  Its all working very nicely. 

On my system I have an unencrypted /boot partition, then a physical partition that is encrypted and used as a container for (any number of) Logical Volumes.   I have root "/", swap, and /home on 3 separate logical volumes.   

My system only asks for a passphrase (sda5_crypt) once, very early in the boot process after GRUB.  (I guess because all the logical volumes are created inside one encrypted container.)

I wonder if you set your system up so that all your partitions (/home and swap) were both inside one encrypted container whether that would guard against the kind of problem you are having now?

---

### Post by megandy on 2008-01-24
Your analysis is correct: I have 2 partionions (with different passphrases). Your idea to put both partitions is not bad if you e.g. use only one system and do not what to "recycle" the swap partition.

Unfortunately, my setup has already 2 container. And the very interesting question is: Where is the configuration file for the order of mounting the encrypted partitions?

---

### Post by tact on 2008-01-24
Agree with you on the interesting question.  :)   While its all working well thats well and good - but I am acutely aware that if things go wrong I have no idea at the moment where to look and what to do. 

I have been reading everything I turn up but apart from "how to install it" there is not a lot of other resource out there yet.  

Have you looked in /etc/crypttab?   It seems to be the crypt partition equivalent of fstab.  Perhaps it effects the loading order?   Mine of course only has one entry in it.

---

### Post by tact on 2008-01-24
I guess having a single container will not suit all needs.  Like your wish to recycle the swap partition.

I have been interested in something I read about having the system generate a random passphrase for the swap at every system restart.  I presume for this to work you must have a separate container for swap also.

---

### Post by megandy on 2008-01-25
> Have you looked in /etc/crypttab? It seems to be the crypt partition equivalent of fstab. Perhaps it effects the loading order? Mine of course only has one entry in it.

Indeed, /etc/crypotab changes the order of mounting your encrypted disks. The problem is, it does not change the order for boot, So, I can change the order of mounting first my swap or my /home, but cannot push up one of them just after the boot loader.

Do you know, where such a question can be placed beside this forum? I thought to post it on launchpad as a bug, but first I want to be sure it's one.. ;)

> I have been interested in something I read about having the system generate a random passphrase for the swap at every system restart. I presume for this to work you must have a separate container for swap also.

That sounds interesting. Do you have a link to that source?

---

### Post by tact on 2008-01-25
You could only try to google and see if you get hits from other distro forums etc.

The first reference I saw to having swap encrypted with a different, random, single use key was on this page:  [http://www.saout.de/misc/dm-crypt/](http://www.saout.de/misc/dm-crypt/)

It is a very brief reference near the end of the document.  

Another good reference I found (tho the configs are not located in the same place in ubuntu) is here:
[http://www.gentoo.org/proj/en/hardened/disk-cryptography.xml](http://www.gentoo.org/proj/en/hardened/disk-cryptography.xml)

There are other resources but I dont have them on hand right now.

---

