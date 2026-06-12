---
title: "RAID + /home mount"
date: 2007-05-20
forum: General Help
---

### Post by rob_quill on 2007-05-20
Hi.

My current PC set up is this:

Single 200GB HDD, nForce 3 motherboard, drive is RAID 0.

However, I am considering partitioning the drvie I have (further), so that I have the follwing partitions:

1. Windows
2. Ubuntu (Feisty)
3. /home
5. backup
6. swap

Despite being top of the list, I wouldnt really mind losing Windows altogether, or shifting all the important data to the /home parition, and massivley reduce the size of that parition, as I virtually never use it. However, that is no small task so may not happen.

Anyway, ideally I'd like to avoid needing to back up anything to do this, i.e. I dont want to have to format the whole drive if it can be avoided. I want a seperate partition for /home so that if I break Ubuntu and have to re-install I will not have lost much/anything. I want a backup partiion so that if anything breaks with the system I can easily restore it/if I accidently delete anything then it is easily recoverable.

Having built this set up, I would like to add an extra drive, and change the RAID level so that the drives mirror each other.

I was wondering if anyone could give me any advice about this? For example, can I make the mount point for /home a seperate partition without reinstalling, as I can only find threads about how to do it from a fresh install? How does changing the RAID level to mirror work when one dirve had data and another is empty? Must the drives be exactly the same size? same make? same spec, e.g. read time etc?

The info I have on backing up is from this thread:

[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

Can I set it up as a cron job? Can I force it to finish before the computer can be shutdown, so that I don't accidently stop the job halfway through?

I realise there are a lot of questions here, and I appreciate any help anyone can give with any of them, as I have never undertaken a hard-drive orgnasation/back-up procedure of this magnitude on before.

Thanks for your help.

Rob

---

### Post by nicepants on 2007-05-23
here's a [link]("http://www.psychocats.net/ubuntu/separatehome") to a howto on how to separate your /home if you've already installed.

=)

---

