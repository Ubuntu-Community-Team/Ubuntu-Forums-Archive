---
title: "I'm Ubuntu and can't figure out how to do a disk check"
date: 2008-02-20
forum: General Help
---

### Post by m8g8 on 2008-02-20
I'm a complete noobie! 

I looked at another thread and someone said 'sudo fsck /dev/xxxx' in the Terminal.

I tried this (it said my HDD was called 299.9 GB Drive or something, so I put that in instead of the X's. Was that right?

It then came with a list of options.

I chose

-n

But it told me that the command doesn't exist.

I'm trying to test this out on my computer, so I can then use it on my brother's (his XP won't start and I want to see if it's a problem with the hard disk)

I would be extremely grateful if anyone could help and explain it in really simple terms.

Also, I've read stuff which mentions ext3. Is this relevant to me? I have tried looking at previous threads but none of this is explained simply enough for me :lolflag:

Thank you!

---

### Post by Mithrilhall on 2008-02-20
Open a terminal and type the following and post back the results.

```

cd /dev
ls

```

The command should be something like (I have a SATA drive):

```

sudo fsck /dev/sda

```

---

### Post by pointone on 2008-02-20
Er... the /dev directory contains EVERY device in the system. "ls /dev" is probably not what you want to do.

The command "cat /etc/fstab" will be more useful; this will show you a complete listing of all the disks mounted by Ubuntu, along with their partition types.

HOWEVER!

FSCK IS VERY DANGEROUS IF YOU DON'T KNOW WHAT YOU'RE DOING!!!

Running fsck on a mounted volume can corrupt the data, and not knowing how to interpret the results/questions may lead to other problems.

---

### Post by seventhc on 2008-02-20
You don't normally need to run anything. Are you having a problem that's making you want to run it?
I think the disk does a check every 25 or 30 boots. Something like that not sure of the exact number.

---

