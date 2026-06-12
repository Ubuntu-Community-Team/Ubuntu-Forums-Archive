---
title: "Can't boot after deleting lockdown.lock file - Boot-repair URL included"
date: 2016-01-17
forum: General Help
---

### Post by Cacique on 2016-01-17
I had a solid working ubuntu system running solid for about a year.   (15.04 > 15.10)

I thought I'd try to backup some data using Deja-Dup.   Deja-Dup gave me an error message and recommended I delete or change permissions on the lockdown.lock file.  (I can't remember exactly as this happened a few weeks ago).   

I just came across the Boot-Repair program and ran that.   My URL is [http://paste.ubuntu.com/14564079](http://paste.ubuntu.com/14564079)

I ran that from a bootable USB drive which is the only way I can get into a working GUI at the moment.   Booting from my hard-drive takes me to a 'busy-box' prompt and I don't know how to fix the problem from there.   

I'd appreciate any help I can get!

Thank-you!

---

### Post by Bucky Ball on 2016-01-18
What is this?

```
sda5: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 
```

It's causing the error 'unknown filesystem' and could be your culprit. Something to do with encryption? I know nothing about encryption, but if so, please, always mention that you are using it if you are. It changes the playing field. 

Please remove other dongles apart from the Boot Repair USB, run the bootinfoscript again and repost the link. Thanks.

---

### Post by Cacique on 2016-01-18
I'm not 100% sure what 'crypto_LUKS' is, but I did encrypt my home directory when I set up my installation of 15.04.   That's the main reason I don't want to just do a fresh re-install as I have data in the encrypted folder I wish to recover...after I get a bootable system again.  

I have removed everything connected to the machine except for the USB I'm running the Live distribution from and of course the internal hard drive which I cannot boot from is still inside the machine.   All other USB ports, SD card ports, and the optical drive are empty now.   

Here is the new bootinfoscript link:   [http://paste.ubuntu.com/14569003/](http://paste.ubuntu.com/14569003/)

Thanks for your help!  Most appreciated!

---

### Post by Bucky Ball on 2016-01-18
From your output:

```
The default repair of the Boot-Repair utility will not act on the MBR.
**Additional repair will be performed:  repair-filesystems**

Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var
**[B]Partition 3 does not start on physical sector boundary.**[/B]
```

I have bolded the important bits. Launch Boot Repair, run the default repair, reboot. That might fix the physical sector boundary.

---

### Post by Cacique on 2016-01-19
I ran the Recommended Repair (default repair) and the system boots to the prompt where it asks me to enter the unlock pass-phrase for the hard disk, then to the Boot Option screen where I can choose *Ubuntu, Rescue, etc., but when I try to boot the system normally it takes me back to the busy-box prompt, which is where I was at before I tried running Boot-Repair.

---

### Post by Bucky Ball on 2016-01-23
*Thread moved to **General Help**.*

As it was posted in the wrong area to begin with (you're not a new user), and considering that, no problem, but generally, no. If your thread hasn't seen any action for about 12 hours, simply post 'bump'. That will take it to the top of search lists again. 

Good luck.

---

### Post by Cacique on 2016-01-29
<snip> 

I really need a solution to this problem and I'm afraid it's beyond my skill-level.  The boot-repair people themselves said they are only giving support now to people who make a donation, but when I enquired as to a suggested amount, twice, I received no response, unfortunately.

---

### Post by Bucky Ball on 2016-01-29
Not sure what this has to do with Boot Repair. Suggest you backup your important data and reinstall if you really can't find your way out of this and no-one is responding, which they haven't for quite awhile.

PS: I posted a clue from your output in post #4 which you may have overlooked:

> Partition 3 does not start on physical sector boundary.

Might not be the cause of your issue but it's an issue. I'd presume that to be sda5 and that says:

>   File system:       crypto_LUKS

... meaning, I think, that it is an encrypted partition, which might also be part of the issue. I know nothing about encrypted partitions having never used one. Further to that:

> Unknown BootLoader on sda5

So, this may mean you have sda5, an encrypted boot partition with an unknown boot loader, not starting on a physical sector boundary.

---

### Post by Cacique on 2016-01-29
Well, the system won't boot, that's why I turned to Boot-Repair.   I ran the "Recommended" repair and it didn't fix the problem.  There are "Advanced" options in the Boot-Repair but the documentation says not to tinker with those settings unless I know what I am doing as I may only make the problem worse.   

I did a regular install of 15.04 and let the installer partition my system.   I didn't customize it, so I have no idea why it on a "physical sector boundary".   Shouldn't it put it one by default?

The only thing I encrypted is my "Home" partition when it gave me the option and I recorded all of the pass-phrases which I can now use to mount the /Home directory using the "ecrypt-filesystem-recover" command and inputting my passphrase.   However, when I try to copy the files to an external hard drive to preserve them, it give me messages that they are read-only files.   

Regarding the unknown Bootloader, I have no clue, I never tried to change the boot-loader so I have to assume it is GRUB2 which I believe is the default boot-loader in 15.04>15.10.  

So, in pointing out to me that I may have "an encrypted boot partition with an unknown boot loader, not starting on a physical sector boundary" is like telling me I have a problem, but what I am asking for is some kind of solution.

---

### Post by Cacique on 2016-01-30
I can get to the encrypted data but it will not let me do anything with it, even when logged in as root (sudo su).   It says I'm not the owner and don't have permission to access it...   
This is far as I can get.   I don't understand user 1000.   I read that is the default user (non-root) and not sure where to go from here.   Thanks in advance.

---

### Post by Bucky Ball on 2016-01-30
As I say, I know nothing about encrypted partitions. Hopefully someone else can get a clue from your info. Keep digging. :)

Please attach large pics (Go Advanced or Adv Reply> paperclip icon). Thanks.

---

### Post by Cacique on 2016-01-30
Just wondering if this appears normal?   I'm wondering if I may have changed my root permissions when I got the lockdown.lock file error...this happened more than a month ago now, so it's difficult to remember.

---

