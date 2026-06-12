---
title: "Grub unable to boot into either Ubuntu or Windows help!"
date: 2016-01-19
forum: General Help
---

### Post by Jamie_Edwards on 2016-01-19
Hi guys,

So I have quite a big issue... I let my computer shut down a week ago thinking everything was ok and dandy, only to find that when I booted it back up earlier this afternoon, I get dropped into grubs "bash-like shell".

Not a problem I thought, and searched this issue online and found two ways to go about fixing it.

The first being that I could use Boot-Repair OR use the terminal.

This is where things get real bad, real fast.

I tried Boot-Repair and it gets to the "purge kernels then reinstall last kernel sdb6(ins). This may require several minutes..." stage and nothing seems to happen for quite some time.

Ok I thought, let's try doing it the good old fashioned way and go through the terminal.

I found the correct partition I'm supposed to mount and subsequently mount it with:

```
:-$ sudo mount /dev/sdb6/ /mnt/
```

Brilliant, it mounts fine! I thought. I'll do the next thing which was:

```
:-$ sudo grub-install --root-directory=/mnt/ /dev/sdb *or* /dev/sdb6
```

And it instantly fails! Something to do with cannot find canonical directory or something or other.

OK, so I try going into the directory it says it cannot get which was: /mnt/dev/boot/

So I try to CD to that directory and it comes up with an:

```
bash: cd: /mnt/boot/: input/output error
```

What does that mean and how do I fix it?

I'd rather not have to install both windows AND ubuntu back onto my SSD again.

---

### Post by Bashing-om on 2016-01-19
Jamie_Edwards; Hello;

Show us what we are working with.
Post back - Between code tags - the outputs of terminal commands :
From the liveDVD
```

sudo parted -l
sudo parted /dev/sda unit s print
sudo parted /dev/sdb unit s print
sudo blkid -c /dev/null

```
If this should turn out to be a UEFI endowed system - then out of my experience range - plenty of others here to assist though -. UEFI is a whole new ball game in the booting arena and nothing prior (MBR) applies.

The warning " bash: cd: /mnt/boot/: input/output error " Might be reason for concern for the condition of the hardware , we will see . Likely is that you have a /boot partition, and trying to install grub to MBR , the re-install of grub will fail.

[INDENT][INDENT]booting
[INDENT][INDENT][INDENT][INDENT]it is a process
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jamie_Edwards on 2016-01-20
I don't actually need to run those commands as I can already confirm that it's a UEFI  system.

And in regards to hardware issue, I hope to god it's not that as my SSD is less than 5 months old (I'm aware of manufacture error and there could be a problem but as it's a Kingston drive).

I've actually gone and re-installed windows as I needed my system running asap.

When I'm next with my PC I'll try re-installing Ubuntu next to windows and try not to muck it up again.

---

