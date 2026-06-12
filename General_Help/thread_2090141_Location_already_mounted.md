---
title: "Location already mounted"
date: 2012-12-01
forum: General Help
---

### Post by Automat2 on 2012-12-01
Hello,
Every time I insert a new blank DVD in my drive, I get a pop-up window that alerts me that this "Location is already mounted".
Then, I have to click "OK" to close this window and continue working with the DVD.
It only happens if I insert a blank DVD. I don't see that pop-up on CD's or DVD movies.
And this is new from Quantal.
Can it be corrected?
Thanks.

---

### Post by dino99 on 2012-12-01
i'm not very sure, but check /etc/fstab and comment out the dvd reader line.
That hardware might be mounted "on demand" when inserting a support ( mountall job), no need to have it mounted in other cases.
( check also your bios in case of special setting about it)

---

### Post by Myglaren on 2012-12-01
I am finding this too.

1st on a newly acquired desktop running QQ 64 bit and since upgrading to QQ 32 bit on my Toshiba laptop it is doing the same - previously it had stopped recognising the DVD drive in the Startup Disc Creator.

I want to Ubuntuize a new Asus laptop that currently has Win7 on it (ptooey) but it won't boot from a dongle so I need a startup disc to install Ubuntu.

Neither of the other machines can burn a disc for me.  CD/DVD Creator will work but the disc won't boot.

---

### Post by Automat2 on 2012-12-02
This is the output of /etc/fstab without a blank DVD in any of my drives. I have two drives, a CD/DVD RW and a CD/DVD player.
> /dev/sda1: UUID="195081b3-dbff-4d34-8fd6-4d112e50b844" TYPE="ext4" 
/dev/sda5: UUID="83327799-dd5a-4ec0-84d2-7917f9206552" TYPE="swap" 
/dev/sdb1: LABEL="Iomega HDD" UUID="D27431CF7431B6D7" TYPE="ntfs" 

And this is the output of /etc/fstab after I have inserted a blank DVD in one of the drives.
> /dev/sda1: UUID="195081b3-dbff-4d34-8fd6-4d112e50b844" TYPE="ext4" 
/dev/sda5: UUID="83327799-dd5a-4ec0-84d2-7917f9206552" TYPE="swap" 
/dev/sdb1: LABEL="Iomega HDD" UUID="D27431CF7431B6D7" TYPE="ntfs" 
I have only one partition  in my HD, native Ubuntu  and "Iomega HDD" is my external HD.

---

### Post by Automat2 on 2012-12-21
> **Myglaren said:**
> 
I want to Ubuntuize a new Asus laptop that currently has Win7 on it (ptooey) but it won't boot from a dongle so I need a startup disc to install Ubuntu.

I don't think you need a start-up disc to install ubuntu, once you have burnt the new system onto a DVD now,  or dongle.
Have you activated the dongle boot in BIOS?

---

