---
title: "Trying to update, system says boot partitions is out of space?"
date: 2015-05-21
forum: General Help
---

### Post by liquidcross on 2015-05-21
I've got a 500GB drive in my Ubuntu 14.04 machine, and after trying to install the latest round of updates (about 200MB) worth, I get an error saying I'm out of disk space. Looking in gparted, there's maybe 150MB left on the boot partition, and over 400GB free on the extended one. I did a standard installation when I initially set up the box, only checking the options to encrypt my home folder and to use LVM.

How can I update now? Why would that boot partition be so tiny as to be nearly useless?

---

### Post by ajgreeny on 2015-05-21
Oh, dear; here we go again!

Have a look at the thread at [http://ubuntuforums.org/showthread.php?t=2278674;](http://ubuntuforums.org/showthread.php?t=2278674;) there's a lot more info there, but come back if you can not sort out your problem from that.

---

### Post by liquidcross on 2015-05-21
> **ajgreeny said:**
> Oh, dear; here we go again!

Have a look at the thread at [http://ubuntuforums.org/showthread.php?t=2278674;](http://ubuntuforums.org/showthread.php?t=2278674;) there's a lot more info there, but come back if you can not sort out your problem from that.

Autoremove seemed to do the trick; the system initially suggested apt-get clean, but that had failed. Thanks for the help! Hopefully this bug gets squashed in a future update.

---

### Post by monkeybrain20122 on 2015-05-21
What is the /boot partition for, again?? Why do so many people set up a /boot partition?

---

### Post by deadflowr on 2015-05-21
> **monkeybrain20122 said:**
> What is the /boot partition for, again?? Why do so many people set up a /boot partition?

It gets setup when you try to do the full disk encryption. (or a plain lvm setup)
It also sets itself up with the tinny tiny size, which is the main cause for all the problems.

You can always add yourself as affects me to [Elfy's Bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093"), if it affects you...

For some reason full disk encryption is enticing.

I've done it once, but found I dislike it.
(I tend to turn on my machine, go do something while it boots, then login.
Full disk encryption needs you to enter a passphrase before the boot sequence begins.
That annoys me)/rant

It also only really keeps the machine safe from physical thefts.
And if you can physically take my machine, you earned it.

Once you unlock the encryption key then the system is as attackable as any other machine.
And you can't use the system until the key is unlock, so...

---

### Post by SeijiSensei on 2015-05-22
If the whole disk were actually encrypted, it would be impossible to boot the system since there would be no program available to decrypt the drive.  So you need a separate unencrypted boot partition to launch the kernel with the initrd image which contains the decryption software.

I never use encryption for the reasons deadflowr presents.

---

