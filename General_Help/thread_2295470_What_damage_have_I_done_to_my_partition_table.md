---
title: "What damage have I done to my partition table?"
date: 2015-09-18
forum: General Help
---

### Post by jdeks on 2015-09-18
I've accidentally run parted's "mklabel" on a GPT drive, as per below:


```
    ubuntu@ubuntu:~s sudo parted 
    GNU Parted 2.3
    Using /dev/sda
    welcome to GNU Parted! Type 'help' to view a list of commands.
    (parted) mklabel
    New disk label type? msdos
    warning: Partition(s) on /dev/sda are being used.
    Ignore/Cancel? I
    warning: The existing disk label on /dev/sdb will be destroyed and 
    all data on this disk will be lost. Do you went to continue?
    Yes/No? y
    Error: Partition(s) 1 on /dev/sda have been written, but we have been 
    unable to inform the kernel of the change, probably because it/they 
    are in use. As a result, the old partition(s) will remain in use. You 
    should reboot now before making further changes.
    lgnore/cancel? c
    (parted)
```

If this was originally a GPT drive, Has this wiped the partion table and written a new MBR table?

How would I then undo this damage?

---

### Post by ajgreeny on 2015-09-19
I am not sure I would call it accidental when you got the warning> warning: The existing disk label on /dev/sdb will be destroyed and 
    all data on this disk will be lost. Do you went to continue?
    Yes/No? y and you still hit the y to continue, but that aside I think you should stop using the disk immediately and try using testdisk on a live system to see if you can recover the partition that you would appear to have now damaged.

---

### Post by jdeks on 2015-09-20
> **ajgreeny said:**
> I am not sure I would call it accidental when you got the warning and you still hit the y to continue, but that aside I...


I'm not sure I'd call that helpfull advice, being snarky and judgemental without knowing the circumstances. But that aside, those commands were run on a LiveCD that arbitrarily decided to change disk labels on me after having spent the whole evening up to that point with the SD card as sda.

For anyone who does find this and wants some helpful advice: yes, mklabel does indeed with the partition table, but you CAN fix it: [http://ubuntuforums.org/showthread.php?t=2289202&page=2&p=13359813#post13359813](http://ubuntuforums.org/showthread.php?t=2289202&page=2&p=13359813#post13359813)

---

### Post by lisati on 2015-09-20
> **ajgreeny said:**
> I am not sure I would call it accidental when you got the warning and you still hit the y to continue, but that aside I think you should stop using the disk immediately and try using testdisk on a live system to see if you can recover the partition that you would appear to have now damaged.

I'm inclined to agree. 

@jdeks: you need to take steps to make sure nothing further gets damaged, so that you are in a better position to recover what you can.

Also see point 3 of [this response]("http://ubuntuforums.org/showthread.php?t=2289202&p=13359686&viewfull=1#post13359686") in your other thread.

---

